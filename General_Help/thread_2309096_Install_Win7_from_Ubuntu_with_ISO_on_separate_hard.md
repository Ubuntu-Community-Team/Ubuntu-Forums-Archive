---
title: "Install Win7 from Ubuntu with ISO on separate hard drive"
date: 2016-01-07
forum: General Help
---

### Post by CinderWild on 2016-01-07
Is that even possible? I've been searching but I can't find anything. Basically just want an Ubuntu version of EasyBCD so I can boot to a Win7 ISO from within Ubuntu 14.04

---

### Post by yancek on 2016-01-07
You can boot a windows installation but you will first need to extract the iso of windows as Grub won't directly boot a windows iso just as no windows will boot a Linux iso.  It is all explained in detail at the link below.  The link explains how to do it on a flash drive but it will work from a partition on another hard drive.  Actually tried this and windows booted and the installer started.  I would definitely read through the page to understand before beginning.

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

