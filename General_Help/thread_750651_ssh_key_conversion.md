---
title: "ssh key conversion"
date: 2008-04-09
forum: General Help
---

### Post by santhosh23 on 2008-04-09
Hi,


I created a pair of public/private keys for ssh-based authetication using puttygen and it is in  SSH-1 format. i would like to convert this keys to a format which openssh understands,i tried to convert it with puttygen and here is what i get 

[root@dhcp-63-12 ~]# puttygen keys/private.ppk -O private-openssh -o internal
puttygen: conversion from SSH-1 to SSH-2 keys not supported



i am not sure what is format for converting ssh-1 keys because i believe private-openssh is used for ssh-2.

please advice

---

### Post by bodhi.zazen on 2008-04-09
puttygen will convert the keys from putty to openssh, but not ssh1 to ssh2

So, make a new key ?

puttygen -t dsa ...

[http://linux.die.net/man/1/puttygen](http://linux.die.net/man/1/puttygen)

You may be able to work arround this by converting the key to an openssh key and then converting the openssh key :

[http://docs.ocf.berkeley.edu/wiki/SSH_key_management#Converting_an_SSH1_key_for_use_with_SSH2](http://docs.ocf.berkeley.edu/wiki/SSH_key_management#Converting_an_SSH1_key_for_use_with_SSH2)

---

