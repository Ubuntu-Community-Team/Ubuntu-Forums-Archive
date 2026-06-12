---
title: "Installation of mdadm fails"
date: 2014-02-08
forum: General Help
---

### Post by colin14 on 2014-02-08
Hi,
New to Ubuntu. Need to mount an array disk and for this I need mdadm. Unfortunately, sudo apt-get install mdadm fails miserably regardless of whether I use 11.04 or 10.0 versions.

The message I get is:

colinhall@ubuntu:~$ sudo apt-get install mdadm
[sudo] password for colinhall: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mdadm is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'mdadm' has no installation candidate
colinhall@ubuntu:~$ 

Any help is greatly appreciated

/Colin

---

### Post by Erik1984 on 2014-02-08
You shouldn't use 11.04 it is no longer supported so fetching packages from the repos doesn't work.

It should be in the repos for currently supported versions.

latest release (13.10): [http://packages.ubuntu.com/saucy/mdadm](http://packages.ubuntu.com/saucy/mdadm)
latest LTS (12.04): [http://packages.ubuntu.com/precise/mdadm](http://packages.ubuntu.com/precise/mdadm)

---

### Post by colin14 on 2014-02-08
Excellent reply, I shall commence DL of named supported release and reattempt installing mdadm.

---

