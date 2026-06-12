---
title: "Is there an idiots guide to Super Grub?"
date: 2007-09-24
forum: General Help
---

### Post by Ramthebuffs on 2007-09-24
I have a laptop that doesn't have a cdr.  I was installing ubuntu and it crashed mid install and now my grub is broken(15).  I'm trying to figure out how to put super grub on a usb but the instructions aren't great for someone like me that isn't great on terminal or linux.  Anyway, I don't want to crash another computer so I'd like some help if anyone knows what to do.

I've put supergrub on my usb inside a boot folder.  The instructions say:
open grub as root 
device (hd3) /dev/ubb # my usb device in linux is called /dev/ubb 
root (hd3,0) 
setup (hd3) 
quit 
reboot 

First of all I'm obviously doing this on a different computer than what I'm going to run the usb on.  I'm a little confused about the hd3 part.  Is this variable from system to system etc?  I'm just concerned that I'm going to kill another computer.  Does anyone have any experience putting supergrub on a usb and running it on a different computer?

Thanks if anyone can help.  I don't like having a $1000 UMPC paperweight.

---

### Post by zvacet on 2007-09-24
Maybe this will help you

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Super_Grub_USB_Disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Super_Grub_USB_Disk")

---

### Post by Ramthebuffs on 2007-09-24
Does it matter what format the usb is?

---

### Post by Shazaam on 2007-09-24
You can also make a SGD floppy...
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_Make_your_Super_Grub_Floppy_Disk](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_Make_your_Super_Grub_Floppy_Disk)

---

