---
title: "QEMU customized kernel version"
date: 2007-04-02
forum: General Help
---

### Post by daniel_camara on 2007-04-02
Hi, people :) 

I have an customized version of linux 2.6.15 kernel with ubuntu. Following the instructions on the page [http://tech.tolero.org/blog/en/linux/qemu-9-and-kqemu-for-ubuntu-dapper-edgy-feisty](http://tech.tolero.org/blog/en/linux/qemu-9-and-kqemu-for-ubuntu-dapper-edgy-feisty) I manage to install the ubuntu in the original 2.6.15 kernel. The problem is that when I try to install it on the customized kernel version I get the following dependency error below.

The name people here gave to the customized distribution it is linux-2.6.15.rtai3.3, However I have NO idea how to create this modules or linux image it depends on. And before I forgot, the /lib/modules/2.6.15.rtai3.3 exists.

I am a little lost here Embarassed . Any Idea? :confused: 

Best regards...

Daniel Camara

----
root@drucifer:~# m-a install kqemu
Selecting previously deselected package kqemu-modules-2.6.15.rtai3.3.
(Reading database ... 174513 files and directories currently installed.)
Unpacking kqemu-modules-2.6.15.rtai3.3 (from
.../kqemu-modules-2.6.15.rtai3.3_1.3.0~pre11-1_i386.deb) ...
dpkg: dependency problems prevent configuration of kqemu-modules-2.6.15.rtai3.3:
kqemu-modules-2.6.15.rtai3.3 depends on linux-modules-2.6.15.rtai3.3 |
linux-image-2.6.15.rtai3.3; however:
Package linux-modules-2.6.15.rtai3.3 is not installed.
Package linux-image-2.6.15.rtai3.3 is not installed.
dpkg: error processing kqemu-modules-2.6.15.rtai3.3 (--install):
dependency problems - leaving unconfigured
Errors were encountered while processing:
kqemu-modules-2.6.15.rtai3.3

I: Direct installation failed, trying to post-install the dependencies

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
kqemu-modules-2.6.15.rtai3.3
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 193kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 174518 files and directories currently installed.)
Removing kqemu-modules-2.6.15.rtai3.3 ...
root@drucifer:~#

-------------------------------------------------

---

