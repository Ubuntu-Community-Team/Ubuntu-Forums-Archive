---
title: "/usr/bin/dpkg-maintscript-helper: basename: not found"
date: 2014-08-23
forum: General Help
---

### Post by viv4 on 2014-08-23
Hi,

I am getting some errors while installing any package on ubuntu 14.10

sudo apt-get install subversion

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libapr1 libaprutil1 libserf-1-1 libsvn1
Suggested packages:
  subversion-tools db5.3-util
The following NEW packages will be installed:
  libapr1 libaprutil1 libserf-1-1 libsvn1 subversion
0 upgraded, 5 newly installed, 0 to remove and 11 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,401 kB of archives.
After this operation, 5,231 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Selecting previously unselected package libapr1:amd64.
(Reading database ... 181177 files and directories currently installed.)
Preparing to unpack .../libapr1_1.5.0-1_amd64.deb ...
Unpacking libapr1:amd64 (1.5.0-1) ...
Selecting previously unselected package libaprutil1:amd64.
Preparing to unpack .../libaprutil1_1.5.3-1_amd64.deb ...
Unpacking libaprutil1:amd64 (1.5.3-1) ...
Selecting previously unselected package libserf-1-1:amd64.
Preparing to unpack .../libserf-1-1_1.3.3-1ubuntu0.1_amd64.deb ...
Unpacking libserf-1-1:amd64 (1.3.3-1ubuntu0.1) ...
Selecting previously unselected package libsvn1:amd64.
Preparing to unpack .../libsvn1_1.8.8-1ubuntu3.1_amd64.deb ...
Unpacking libsvn1:amd64 (1.8.8-1ubuntu3.1) ...
Preparing to unpack .../subversion_1.8.8-1ubuntu3.1_amd64.deb ...
/usr/bin/dpkg-maintscript-helper: 528: /usr/bin/dpkg-maintscript-helper: basename: not found
dpkg: error processing archive /var/cache/apt/archives/subversion_1.8.8-1ubuntu3.1_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/subversion_1.8.8-1ubuntu3.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

