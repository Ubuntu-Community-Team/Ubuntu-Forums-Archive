---
title: "anberra-gtk-module missing"
date: 2013-09-27
forum: General Help
---

### Post by digimark on 2013-09-27
HI All,

I had an error in termail stating that the above was not loaded or not found.

I installed libcanberra-gtk3-module or tried to but i get the following error

user@ChrUbuntu:~$ sudo apt-get install libcanberra-gtk3-moduleReading package lists... Done
Building dependency tree       
Reading state information... Done
libcanberra-gtk3-module is already the newest version.
The following packages were automatically installed and are no longer required:
  libgtkhtml-4.0-common libpst4 bogofilter-bdb xdotool libgtkhtml-4.0-0
  evolution-common libgtkhtml-editor-4.0-0 bogofilter-common libxdo2
  bogofilter libgsl0ldbl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up icaclient (12.1.0) ...
dpkg: error processing icaclient (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of ctxusb:
 ctxusb depends on icaclient; however:
  Package icaclient is not configured yet.
dpkg: error processing ctxusb (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 icaclient
 ctxusb
E: Sub-process /usr/bin/dpkg returned an error code (1)


please any advice would be appreciated.

thanks

---

### Post by chamuco107 on 2013-09-27
Hi digimark,

By looking at your error messages, you need to configure and install icaclient as it is a dependacy for ctxusb. Please visit [http://plone.uconn.edu/workspaces/uits-linux/facts/installing-citrix-icaclient-on-64bit-ubuntu-12.04](http://plone.uconn.edu/workspaces/uits-linux/facts/installing-citrix-icaclient-on-64bit-ubuntu-12.04) for install instructions assuming your running 64-bit Ubuntu 12.04. If you do not have this version please reply back with correct Ubuntu version and I will try my best to point you in the right direction for install instructions.

---

### Post by digimark on 2013-09-27
HI Chamuco,

Thanks for coming back....and the ink...im afraid no use.....

following the instructions I had an error


user@ChrUbuntu:~$ sudo apt-get lib32gccl ia32-libs
E: Invalid operation lib32gccl
user@ChrUbuntu:~$ sudo apt-get install lib32gccl ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package lib32gccl

still icarried n and tried the next one...which also failed as it couldnt find the ica

then tried to apt get install the ica client and the error message was E: Unable to locate package icaclient-12.1.0_i386.deb
E: Couldn't find any package by regex 'icaclient-12.1.0_i386.deb'

thanks for your help....

---

