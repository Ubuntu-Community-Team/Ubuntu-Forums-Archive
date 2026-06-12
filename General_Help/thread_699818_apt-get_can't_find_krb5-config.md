---
title: "apt-get can't find krb5-config"
date: 2008-02-17
forum: General Help
---

### Post by zorrek on 2008-02-17
I'm setting up U 6.10 to connect to an AD domain.
All is going smoothly until I have to install krb5-config


root@inara:/etc/samba# apt-get install krb5-config
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package krb5-config

source list is:
deb cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release Candidate i386 (20061017.1)]/ edgy main restricted

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

I've done apt-get update and upgrade all went well.

I'm stuck

---

### Post by bwhite82 on 2008-02-17
Hmm, that's odd. I see it as being in the Universe repo. At any rate, here is a direct link for the edgy package:

[http://mirrors.kernel.org/ubuntu/pool/universe/k/kerberos-configs/krb5-config_1.10_all.deb](http://mirrors.kernel.org/ubuntu/pool/universe/k/kerberos-configs/krb5-config_1.10_all.deb)

---

### Post by zorrek on 2008-02-17
I'll give that a shot after further reading I tried this

root@inara:/etc/samba# apt-get install krb5-user
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package krb5-user is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  krb5-doc
E: Package krb5-user has no installation candidate

krb5-user is supposed to install krb5.conf

---

