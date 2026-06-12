---
title: "defining usb as root file system-advanced question"
date: 2014-03-07
forum: General Help
---

### Post by rburkartjo on 2014-03-07
i have no iso burn program on my hard drive for my cdrom. i wanted to install an iso completely on a 32 gig usb stick. so i put the iso on small 8 gig stick then formated my 32 gig stick to ext4. then booted the usb stick and clicked on the install button and selected a custom install. the options to install came up as my hard drive and 32 gig stick. however, when i selected the stick i get the error message no root file system is defined pls correct from the partitioning menu. any ideas. tks

---

### Post by dragonfly41 on 2014-03-07
You could try** unetbootin** to create your bootable USB device ..
it is in Ubuntu Software Centre

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by rburkartjo on 2014-03-07
tks dragon i know i can do that for a live cd. what i was trying to do was to make a full install on my usb stick however keep getting the aforementioned error message. maybe it cant be done.

---

### Post by 3rdalbum on 2014-03-07
You forgot to actually tell the installer where to put Ubuntu. Select the USB stick and choose "Edit Partition". Set the mount point to / and you can continue with the installation.

Installing the system onto a USB flash drive will put unusual wear and tear on the USB. Keep a backup of your data or use a hard disk instead of a flash drive.

---

### Post by rburkartjo on 2014-03-08
tks 3rd that did the trick. was searching for a few days to find the answer. cant believe that i overlook the obvious. also had to run my boot repair disk after i installed. works like a charm

---

