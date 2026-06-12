---
title: "Permission denied error when installing MATLAB"
date: 2015-02-05
forum: General Help
---

### Post by eljc2 on 2015-02-05
Hi

I am trying to install a student version of MATLAB and Simulink on xubuntu from a CD-ROM.

I don't have a CD drive in my computer, so I've copied the files across to my desktop.

I am getting the following error when trying to run the install script:

john@ASUS-red:~/Desktop/MATLAB$ ls
autorun.inf  InstallForMacOSX.app  install_unix.sh  setup.exe  unix  win32
john@ASUS-red:~/Desktop/MATLAB$ sudo ./install_unix.sh
[sudo] password for john: 
./install_unix.sh: 4: exec: ./unix/install: Permission denied

I have ticked 'Allow this file to run as a program' in the Permissions properties tab.

Here's what's in the install_unix.sh file:

#! /bin/sh 
dirs=`dirname $0`
args=$@
exec $dirs/unix/install -nocp $args

---

