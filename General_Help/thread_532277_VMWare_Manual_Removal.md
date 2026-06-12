---
title: "VMWare Manual Removal"
date: 2007-08-22
forum: General Help
---

### Post by ashughes on 2007-08-22
I cannot seem to get vmware player to be completely purged from my system.  I am trying to get VMWare workstation installed and can successfully do it, but Ubuntu still thinks that Player is installed.  So every time I reboot, I have to reconfigure workstation.

This is my results of **dpkg -l | grep vmware**:
pF vmware-player 1.0.2-2 Free virtual machine player from VMware
rc vmware-tools-kernel-modules-2.6.20-16 2.6.20.5-16.29 vmware-tools modules for Linux (kernel 2.6.20)
ii xserver-xorg-video-vmware 10.15.0-0ubuntu1 X.Org X server -- VMware display driver

Sorry for the spacing...I couldnt get it to work right.

Anyway, at this point I am considering just wiping my drive and reloading ubuntu.  Any ideas on how I can fix this?  I want to be using Workstation exclusively.

Thanks.

---

### Post by ashughes on 2007-08-22
PS.

Doing an ls -Rl * | grep vmware* from / returns no results.  So I know there is no instance of VMWare left.

Any ideas?

---

