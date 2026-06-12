---
title: "Trying to create windows 10 partition alongside Ubuntu"
date: 2018-06-07
forum: General Help
---

### Post by casparwylie on 2018-06-07
[COLOR=#111111][FONT=inherit]I currently am running Ubuntu 18.04 LTS on an Dell XPS 15 (9560). My aim is to have two options every time I boot the computer: Ubuntu, or Windows 10.[/FONT][/COLOR]
[COLOR=#111111][FONT=inherit]I have already created a bootable windows 10 usb. I did this by using Gparted to make the usb stick of type NTFS, and adding boot flags to make it bootable. I then used UNetbootin, to install latest Windows 10 64bit IOS file onto the usb stick. This seemed to work. My attachment shows the usb stick (64 GB Thumb Drive) as NTFS with BIOS Boot type, it shows the new contents of the usb stick on the left (does that look like it contains the correct files?).[/FONT][/COLOR]
[COLOR=#111111][FONT=inherit][ATTACH=CONFIG]280025[/ATTACH]

I want to make sure my current Ubuntu running remains the same, keeps all files and accounts.[/FONT][/COLOR]
[COLOR=#111111][FONT=inherit]The problem is, when I boot up the computer holding f12, with the usb plugged in, nothing representing the windows10 usb appears.[/FONT][/COLOR]
[COLOR=#111111][FONT=inherit]The things that do appear are:[/FONT][/COLOR]
[COLOR=#111111][FONT=inherit]**LEGACY BOOT:**[/FONT][/COLOR]
[COLOR=#111111][FONT=inherit]**USB Storage Device** (this does not work at all, and says something like "missing operating system" when i select it. Interestingly, if the usb stick isn't plugged in, this option does not appear.)[/FONT][/COLOR]
[COLOR=#111111][FONT=inherit]**USB NIC**[/FONT][/COLOR]
[COLOR=#111111][FONT=inherit]**UEFI BOOT:**[/FONT][/COLOR]
[COLOR=#111111][FONT=inherit]**ubuntu**[/FONT][/COLOR]
[COLOR=#111111][FONT=inherit]**UEFI: THNSHFF** (etc etc.....)[/FONT][/COLOR]
[COLOR=#111111][FONT=inherit]I have tried all different boot modes, nothing works. In fact, selecting any of the options above fail in some way. The only way I can get back onto my Ubuntu Desktop is to restart, and not press f12. I also noticed in Disks (see screenshot) that the main 59GB part of the 64GB (sda2) has Windows installed, but there is actually a sda1 containing 211 MG. Perhaps this is getting in the way?[/FONT][/COLOR]
[COLOR=#111111][FONT=inherit]I also noticed the many different options for Edit Partition > Type, perhaps its one of these: 
[ATTACH=CONFIG]280024[/ATTACH][/FONT][/COLOR]
[COLOR=#111111][FONT=inherit]My question is, assuming my usb stick contents looks correct for Windows 10, what should I do to confirm it appears on boot?[/FONT][/COLOR]
[COLOR=#111111][FONT=inherit]If it doesn't look correct (but I think it does), what is the best way to create a bootable USB Windows 10, on Ubuntu? (WoeUSB does not work)[/FONT][/COLOR]

---

### Post by yancek on 2018-06-07
If you read the unetbootin home page you will see that it is to create a Linux bootable usb, it will not work with windows.  If you have Ubuntu already installed, make sure you have unallocated space on whichever drive you wish to install windows and use the Custom install option in windows booting from a DVD.  If you do not have a DVD, you can create a bootable use of windows with the instructions at the following page:

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

You can skip the part about installing grub on the flash drive and simply put the entry in your current Ubuntu grub.cfg fileu

---

### Post by oldfred on 2018-06-08
You have an UEFI system, and will want Windows installed in UEFI boot mode.
UEFI only boots from FAT32 partitions, not NTFS.
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/install-windows-from-a-usb-flash-drive](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/install-windows-from-a-usb-flash-drive)
Should be same for Windows 10:
[https://www.eightforums.com/threads/uefi-bootable-usb-flash-drive-create-in-windows.15458/](https://www.eightforums.com/threads/uefi-bootable-usb-flash-drive-create-in-windows.15458/)

And once installed you have different partitions:
       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

