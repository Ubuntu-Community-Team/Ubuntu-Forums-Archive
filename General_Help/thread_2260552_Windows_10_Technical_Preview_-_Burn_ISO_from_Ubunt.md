---
title: "Windows 10 Technical Preview - Burn ISO from Ubuntu"
date: 2015-01-12
forum: General Help
---

### Post by Tristan_Williams on 2015-01-12
Ubuntu Studio 14.10

Downloaded Windows 10 Technical Preview ISO, want to burn to USB so I can install to secondary HDD.
Unetbootin does not work for burning Windows ISO's.

How do I burn the ISO to USB from Ubuntu?

---

### Post by yancek on 2015-01-12
Check the link below which explains how to create a bootable windows from an iso.  I did this with Windows Technical Preview and was able to boot the flash with it on and start the install.  Didn't finish the install because I only had a usb drive to install to and it wouldn't install, got this message:  "windows setup does not support configuration or installation to a disk connected through usb or IEEE 1394 ports".

One problem I had was with the Disk Image Mounter.  When I tried to use it, it produced an error indicating the iso was too large, 2.9GB so I loop mounted it and then copied all these files/folders to the flash drive.  If you use this method, read carefully and you MUST copy the windows files to the flash first and verify they are there before trying to install Grub.  You should be able to boot from the flash to install.

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

### Post by Bucky Ball on 2015-01-12
If you have a DVD, Brasero? Not sure if that is installed by default in UStudio, though. It is in the repos.

---

### Post by pqwoerituytrueiwoq on 2015-01-12
i used a virtualbox to do this and accessed the ISO via network share in windows last time

---

### Post by yancek on 2015-01-12
I'd recommend VirtualBox before going through all the hassle of installing a test system like windows 10.  Much simpler, all you need to boot it is the iso which you already have.

---

