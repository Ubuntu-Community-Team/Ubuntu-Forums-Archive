---
title: "[SOLVED] emerald theme manager"
date: 2008-06-18
forum: General Help
---

### Post by Ryklou on 2008-06-18
i was wondering where and what i need to download emerald theme manager. i've been looking for this forever.

tnx

~francois

---

### Post by Qrikko on 2008-06-18
errr.. you actually should have Emerald in the repos:

sudo apt-get install emerald

or using synaptic.

or did I missunderstand the question?
Really sorry if I am missunderstanding :) but we are talking Emerald theme for Beryl right? I am pretty sure you only need to apt-get it.

---

### Post by Ryklou on 2008-06-18
```
francois@ShadowGFX-Linux:~$ clear
francois@ShadowGFX-Linux:~$ sudo apt-get install emerald
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libemeraldengine0
Recommended packages:
  emerald-themes
The following NEW packages will be installed:
  emerald libemeraldengine0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 342kB of archives.
After this operation, 1712kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com hardy/universe libemeraldengine0 0.7.2-0ubuntu2 [80.5kB]
Get:2 http://us.archive.ubuntu.com hardy/universe emerald 0.7.2-0ubuntu2 [261kB]
Fetched 342kB in 1s (288kB/s)
Selecting previously deselected package libemeraldengine0.
(Reading database ... 128680 files and directories currently installed.)
Unpacking libemeraldengine0 (from .../libemeraldengine0_0.7.2-0ubuntu2_i386.deb) ...
Selecting previously deselected package emerald.
Unpacking emerald (from .../emerald_0.7.2-0ubuntu2_i386.deb) ...
Setting up libemeraldengine0 (0.7.2-0ubuntu2) ...

Setting up emerald (0.7.2-0ubuntu2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```

No actually you helped me, TY

---

