---
title: "broken package problems"
date: 2006-08-06
forum: General Help
---

### Post by xboxbman on 2006-08-06
I'm a little new to linux, but I'd like to think that I'm learning quick.  I have been getting a broken package erro everytime I try to update.  Here's what it says when I do ap-get to try to get the broken packeages

bman@bman-desktop:~$ sudo apt-get install libmjpegtools0c2a
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  libmjpegtools0c2a
0 upgraded, 1 newly installed, 0 to remove and 47 not upgraded.
2 not fully installed or removed.
Need to get 0B/205kB of archives.
After unpacking, 541kB of additional disk space will be used.
(Reading database ... 116877 files and directories currently installed.)
Unpacking libmjpegtools0c2a (from .../libmjpegtools0c2a_1%3a1.8.0-0.0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libmjpegtools0c2a_1%3a1.8.0-0.0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libmjpegutils-1.8.so.0.0.0', which is also in package libmjpegtools0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libmjpegtools0c2a_1%3a1.8.0-0.0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


what do I do to deal with this?  I've been trying to fix this on my own, but I obviously have no clue what I'm doing....All help is greatly appreciated!

---

### Post by vijirajan on 2006-08-06
It looks like you already have a package named "libmjpegtools0" installed that shares files with the package you are trying to install. Uninstall "libmjpegtools0" before installing "libmjpegtools0c2a".

Hope this helps!

---

### Post by xboxbman on 2006-08-07
> **vijirajan said:**
> It looks like you already have a package named "libmjpegtools0" installed that shares files with the package you are trying to install. Uninstall "libmjpegtools0" before installing "libmjpegtools0c2a".

Hope this helps!

worked perfectly!  Thanks for the help.

---

