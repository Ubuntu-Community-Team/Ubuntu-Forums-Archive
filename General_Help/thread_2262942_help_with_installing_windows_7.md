---
title: "help with installing windows 7"
date: 2015-01-28
forum: General Help
---

### Post by shelby3 on 2015-01-28
I've been trying for two days now to install Windows 7, I've  used the UNetbootin and Gparted to get the iso file onto my usb. But instead of ntfs, Unetbootin only recognizes it as FAT32, which doesn't work. So I simply dragged the iso file directly onto the usb, which got me further to the point where I can try to install from it from the boot window, but I end up with the message bootmgr missing or something saying bootmgr isn't there, really need help with this, I've searched non stop for how to fix it, but everything I find doesn't work, computer is the bf's and he doesnt have the windows 7 disc, so it has to be done through usb. Any help is greatly appreaciated, not too many computers I can't figure out, except this one :(

---

### Post by stalkingwolf on 2015-01-28
if you have an ISO burn it to a disk with k3b.   I have never had any luck with win7 on a usb.  There might be a rescue partition you can install from.

---

### Post by yancek on 2015-01-28
Unetbootin needs FAT32, I think it says that right on their home page.
I doubt very much that it will work trying to boot just the windows iso file because there is no bootloader in the mbr of the flash.  Take a look at the link below which explains how to do it booting the flash drive with Grub and the windows files extracted and put on the flash drive.  Read it over a few times if it isn't familiar at first.  I tried it with Windows 10 Tech Preview and the only problem I had was the Disk Image Mounter wouldn't extract the files because the iso was almost 3GB.  Otherwise, no problem booting it.  

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

