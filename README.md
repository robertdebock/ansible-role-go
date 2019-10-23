go
=========

<img src="https://docs.ansible.com/ansible-tower/3.2.4/html_ja/installandreference/_static/images/logo_invert.png" width="10%" height="10%" alt="Ansible logo" align="right"/>
<a href="https://travis-ci.org/robertdebock/ansible-role-go"><img src="https://travis-ci.org/robertdebock/ansible-role-go.svg?branch=master" alt="Build status" align="left"/></a>

Install go on your system.

<img src="https://img.shields.io/ansible/role/d/34937"/>
<img src="https://img.shields.io/ansible/quality/34937"/>

Example Playbook
----------------

This example is taken from `molecule/resources/playbook.yml`:
```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: yes

  vars:
    go_packages:
      - github.com/golang/dep

  roles:
    - robertdebock.go
```

The machine you are running this on, may need to be prepared.
```yaml
---
- name: Prepare
  hosts: all
  gather_facts: no
  become: yes

  roles:
    - role: robertdebock.bootstrap
    - role: robertdebock.core_dependencies
    - role: robertdebock.buildtools
    - role: robertdebock.git
```

Also see a [full explanation and example](https://robertdebock.nl/how-to-use-these-roles.html) on how to use these roles.

Role Variables
--------------

These variables are set in `defaults/main.yml`:
```yaml
---
# defaults file for go

# Verion to install.
go_version: 1.11.2

# Where to place go
go_destination: /usr/local

# Where to download packages to, aka GOROOT.
go_path: /root/go
```

Requirements
------------

- Access to a repository containing packages, likely on the internet.
- A recent version of Ansible. (Tests run on the current, previous and next release of Ansible.)

The following roles can be installed to ensure all requirements are met, using `ansible-galaxy install -r requirements.yml`:

```yaml
---
- robertdebock.bootstrap
- robertdebock.core_dependencies
- robertdebock.buildtools
- robertdebock.git

```

This role uses the following modules:
```yaml
---
- command
- file
- package
- template
- unarchive
```

Context
-------

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/drawings/artifacts/go.png "Dependency")


Compatibility
-------------

This role has been tested on these [container images](https://hub.docker.com/):

|container|tag|allow_failures|
|---------|---|--------------|
|docker-alpine-openrc|latest|no|
|docker-alpine-openrc|edge|yes|
|docker-debian-systemd|stable|yes|
|docker-debian-systemd|unstable|yes|
|docker-debian-systemd|latest|no|
|docker-centos-systemd|7|no|
|docker-redhat-systemd|7|no|
|docker-centos-systemd|latest|no|
|docker-redhat-systemd|latest|no|
|docker-fedora-systemd|latest|no|
|docker-fedora-systemd|rawhide|yes|
|docker-opensuse-systemd|latest|no|
|docker-ubuntu-systemd|rolling|yes|
|docker-ubuntu-systemd|devel|yes|
|docker-ubuntu-systemd|latest|no|

This role has been tested on these Ansible versions:

- ansible~=2.7
- ansible~=2.8
- git+https://github.com/ansible/ansible.git@devel

The indicator '\~=' means [compatible with](https://www.python.org/dev/peps/pep-0440/#compatible-release). For example 'ansible\~=2.8' would pick the latest ansible-2.8, for example ansible-2.8.6.


Included version(s)
-------------------

This role [refers to a version](https://github.com/robertdebock/ansible-role-go/blob/master/defaults/main.yml) released by Go. Check the released version(s) here:
- [go](https://golang.org/dl/).

This version reference means a role may get outdated. Monthly tests occur to see if [bit-rot](https://en.wikipedia.org/wiki/Software_rot) occured. If you however find a problem, please create an issue, I'll get on it as soon as possible.

Testing
-------

[Unit tests](https://travis-ci.org/robertdebock/ansible-role-go) are done on every commit and periodically.

If you find issues, please register them in [GitHub](https://github.com/robertdebock/ansible-role-go/issues)

To test this role locally please use [Molecule](https://github.com/ansible/molecule):
```
pip install molecule
molecule test
```

To test on Amazon EC2, configure [~/.aws/credentials](https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/credentials.html) and set a region using `export AWS_REGION=eu-central-1` before running `molecule test --scenario-name ec2`.

There are many specific scenarios available, please have a look in the `molecule/` directory.

License
-------

Apache-2.0


Author Information
------------------

[Robert de Bock](https://robertdebock.nl/)
