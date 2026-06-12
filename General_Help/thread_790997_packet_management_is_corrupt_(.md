---
title: "packet management is corrupt :("
date: 2008-05-11
forum: General Help
---

### Post by pedrotuga on 2008-05-11
anyideas to solve this problem?
Is it possible to rebuild the dependence tree or something like that?


```
$ sudo apt-get install curl
[sudo] password for p:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libcurl3
The following NEW packages will be installed:
  curl libcurl3
0 upgraded, 2 newly installed, 0 to remove and 21 not upgraded.
Need to get 0B/357kB of archives.
After unpacking 680kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: parse error, in file `/var/lib/dpkg/available' near line 2 package `xmodmap':
 value for `status' field not allowed in this context
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by Stemp on 2008-05-11
Try with a sudo dpkg --clear-avail && sudo apt-get update

---

### Post by pedrotuga on 2008-05-12
Yay, that worked!
Thanks.

---

