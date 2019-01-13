## Minimal Alpine LInux with Openssh server

[![Build Status](https://travis-ci.org/titom73/docker-sshd.svg?branch=master)](https://travis-ci.org/titom73/docker-sshd)
[![](https://images.microbadger.com/badges/image/inetsix/sshd.svg)](https://microbadger.com/images/inetsix/sshd "Get your own image badge on microbadger.com")
![](https://img.shields.io/docker/pulls/inetsix/sshd.svg)

### Overview

Use this Dockerfile / -image to start a sshd-server upon a lightweight Alpine container.

### Features
* Always installs the latest OpenSSH-Version available for Alpine
* Password of "root"-user can be changed when starting the container using --env
* You can choose between ssh-keypair- and password auth

### Basic Usage
#### Authentication by password
```
$ docker run --rm \
  --publish=1337:22 \
  --env ROOT_PASSWORD=MyRootPW123 \
  inetsix/sshd
```

After the container is up you are able to ssh in it as root with the in --env provided password for "root"-user.

```
$ ssh root@mydomain.tld -p 1337
```

#### Authentication by ssh-keypair

```
$ docker run --rm \
  --publish=1337:22 \
  --env KEYPAIR_LOGIN=true \
  --volume /path/to/authorized_keys:/root/.ssh/authorized_keys \
  inetsix/sshd
```

After the container is up you are able to ssh in it as root with a private-key which matches the provided public-key in authorized_keys for "root"-user.

```
$ ssh root@mydomain.tld -p 1337 -i /path/to/private_key
```
