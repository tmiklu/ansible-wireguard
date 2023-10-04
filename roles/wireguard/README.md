Role Name
=========

A brief description of the role goes here.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

requirements.yml

```
---
roles:
  - name: wireguard
    src: https://github.com/tmiklu/ansible-wireguard.git
    version: main
    scm: git
```

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```
---
- hosts: wireguard
  gather_facts: no
  become: yes
  roles:
    - wireguard
  vars:
    users:
      - name: "tomas.miklusicak"
        ip: "192.168.100.10/32"
        pubkey: "OTyanWqP4jJY8AhuCk88lFIfqkNtPKPuFDemMhJF0x0="
      - name: "frantisek.petr"
        ip: "192.168.100.11/32"
        pubkey: "VIMW39knTaC4J3hoQjQ+VbUAXg4DMaIeepjrvz+T1Vw="

    network_device: "ens5"
    dns_resolver: "10.0.0.2"
    allowed_ips: "10.0.0.0/16"
    endpoint: "3.75.37.152"
    wireguard_private_key: "{{ lookup('amazon.aws.aws_secret', 'emeldi-master-ec2-wireguard-cryptographic-keys.privatekey', nested=True) }}"
    wireguard_public_key: "{{ lookup('amazon.aws.aws_secret', 'emeldi-master-ec2-wireguard-cryptographic-keys.publickey', nested=True) }}"
    wireguard_preshared_key: "{{ lookup('amazon.aws.aws_secret', 'emeldi-master-ec2-wireguard-cryptographic-keys.presharedkey', nested=True) }}"
```

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
