---
title: "Cant re-install libsvn1 after disk crash"
date: 2008-03-28
forum: General Help
---

### Post by JulesBl on 2008-03-28
Hi

My hardisk had some problems due to power supply going phut.

One of the results has been a corruption of my svn libraries, I have been  attempting to re-install them, but I get this

=======================================

julianb@julianb-desktop-main:~$ sudo apt-get install libsvn1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglitz-glx1 libezv24-0 libglitz1 python-wxversion python-wxgtk2.6
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed
  libsvn1
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/602kB of archives.
After unpacking 1405kB of additional disk space will be used.
(Reading database ... 116526 files and directories currently installed.)
Unpacking libsvn1 (from .../libsvn1_1.4.4dfsg1-1ubuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libsvn1_1.4.4dfsg1-1ubuntu3_i386.deb (--unpack):
 unable to make backup link of `./usr/lib/libsvn_fs-1.so.1.0.0' before installing new version: Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libsvn1_1.4.4dfsg1-1ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

======================================================

So, as far as I can tell it wont let me re-install because it cant find the original to backup, is there any way round this?

Jules

---

