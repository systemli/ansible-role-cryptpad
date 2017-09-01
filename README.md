# ansible-role-cryptpad

[![Build Status](https://travis-ci.org/systemli/ansible-role-cryptpad.svg?branch=master)](https://travis-ci.org/systemli/ansible-role-cryptpad) [![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-cryptpad-blue.svg)](https://galaxy.ansible.com/systemli/cryptpad/)

Install and maintain an [Cryptpad](https://cryptpad.fr/) service.

This role will setup an cryptpad service running on 0.0.0.0:3000.

You need to have a running webserver with a vhost pointing to your cryptpad instance and it's port. 

## Role Variables

Defaults:

    # Playbook variables
    cryptpad_required_packages:
      - nodejs
      - git
    
    cryptpad_repository: "https://github.com/xwiki-labs/cryptpad.git"
    cryptpad_repository_key_file: ""
    cryptpad_repository_version: "master"
    cryptpad_user: "cryptpad"
    cryptpad_group: "{{ cryptpad_user }}"
    cryptpad_home: "/home/cryptpad"
    cryptpad_path: "{{ cryptpad_home }}/cryptpad"
    cryptpad_update: False
    
    # template/config.js variables
    cryptpad_http_address: "::"
    cryptpad_http_headers_enabled: True
    cryptpad_content_security_enabled: True
    cryptpad_pad_content_security_enabled: True
    cryptpad_http_port: 3000
    cryptpad_http_safe_port: 3001
    cryptpad_websocket_path: "/cryptpad_websocket"
    cryptpad_log_to_stdout: "false"
    cryptpad_verbose: "false"
    cryptpad_main_pages:
      - index
      - privacy
      - terms
      - about
      - contact
      - what-is-cryptpad
    
    cryptpad_remove_donate_button: "false"
    cryptpad_allow_subscriptions: "false"
    cryptpad_domain: "i.did.not.read.my.config.myserver.tld"
    cryptpad_default_storage_limit: "50 * 1024 * 1024"
    cryptpad_admin_email: "i.did.not.read.my.config@cryptpad.fr"
    cryptpad_storage: "./storage/file"
    cryptpad_file_path: "./datastore/"
    cryptpad_pin_path: "./pins"
    cryptpad_blob_path: "./blob"
    cryptpad_blob_staging_path: "./blobstage"
    cryptpad_channel_expiration_ms: 30000
    cryptpad_open_file_limit: 2048
    cryptpad_rpc: "./rpc.js"
    cryptpad_suppress_rpc_errors: "false"
    cryptpad_enable_uploads: "true"
    cryptpad_max_upload_size: "20 * 1024 * 1024"
    
    # enable monit service monitoring
    cryptpad_monit_enabled: False

## Download


Download latest release with `ansible-galaxy`

	ansible-galaxy install systemli.cryptpad

## Example Playbook


    - hosts: servers
      roles:
         - { role: systemli.cryptpad }



## Testing

Make sure your user is in the `docker` group. To only test your current setup, do

    molecule test

To test different versions of ansible, do

    tox

If your role depends on other roles from [Ansible Galaxy](https://galaxy.ansible.com/), uncomment the dependency lines in `molecule.yml` and add the dependencies in `tests/requirements.yml`.

## License

GPL

## Author Information

https://www.systemli.org
