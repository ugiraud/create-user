Create User
=========

A simple role which creates a user and some folders, used as an example in an ansible training

Requirements
------------

None

Role Variables
--------------

__Required variables:__

user_name: Name of the target user


__Defaults:__

home_directory: /home
user_password: "{{ lookup('password', '{{ user_name }} length=16') | password_hash('sha512', 'salty') }}"
user_comment: "Ansible managed user"
user_shell: /bin/bash
user_id: 1000
main_group:
  name: users
  gid: 1000

Dependencies
------------

None

Example Playbook
----------------

```
- name: create user
  hosts: all
  tasks:
    - name: "Include create_user"
      include_role:
        name: "create_user"
      vars:
        user_name: myUser
```

License
-------

BSD
