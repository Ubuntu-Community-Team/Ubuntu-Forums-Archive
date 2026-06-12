---
title: "dpkg error, please help.. code 2"
date: 2014-02-28
forum: General Help
---

### Post by Hrvoje_Herceg on 2014-02-28
Trying to install gparted but i get error:

herc@herc-MacBook ~ $ sudo apt-get install gparted
[sudo] password for herc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  squid-langpack squid3 squid3-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgtkmm-2.4-1c2a
Suggested packages:
  xfsprogs reiserfsprogs reiser4progs jfsutils ntfsprogs yelp kpartx dmraid gpart
The following NEW packages will be installed:
  gparted libgtkmm-2.4-1c2a
0 upgraded, 2 newly installed, 0 to remove and 13 not upgraded.
Need to get 1,553 kB of archives.
After this operation, 5,837 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main libgtkmm-2.4-1c2a i386 1:2.24.2-1ubuntu2 [1,018 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main gparted i386 0.12.1-1 [535 kB]            
Fetched 1,553 kB in 11s (136 kB/s)                                                             
dpkg: error: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)

Please help!
Thank you

---

### Post by Elfy on 2014-02-28
Thread closed. Please do not post duplicates, it dilutes community effort.

---

