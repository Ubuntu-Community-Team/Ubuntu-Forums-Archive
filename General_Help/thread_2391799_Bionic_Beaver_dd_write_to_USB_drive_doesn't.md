---
title: "Bionic Beaver dd write to USB drive doesn't"
date: 2018-05-13
forum: General Help
---

### Post by dpg1 on 2018-05-13
Long time Linux user.  I rebuilt my 16.04 and installed 18.04 fresh install. and I am now having trouble using dd to copy disk images to USB flash drives.

It is acting like it is caching disk access and not flushing, even after issuing a sync.  


I'm trying to write a Raspberry Pi disk image to a micro SD in a USB adapter.  I've done this dozens of times on many versions of Linux.
But today I'm stumped why it doesn't write out to the disk on this version

Any advice would be appreciated.

Thanks

---

### Post by dino99 on 2018-05-13
are sure about the usb's path, its attribute :confused:

---

### Post by dpg1 on 2018-05-14
> **dino99 said:**
> are sure about the usb's path, its attribute :confused:

Great point.  Yes, I feel that I know the drive location.

/dev/sda is my original 1TB 16.04 drive that I mount as an extra drive to reference old files.
/dev/sdb is my current 18.04 boot disk which is a 60G SSD
/dev/sdc is where USB disks are attached.   I add a USB which is formatted already with RetroPi and Beaver automounts those drives /dev/sdc1 and /dev/sdc2 onto /media/*

I manually umount those drives (not eject)  and then dd a drive image to /dev/sdc.

I write 600M RasPlex image to that drive and it completes almost immediate (first warning sign).  I sync and it returns immediately (even stranger).

I dd back from /dev/sdc into a local file (also instantaneous) and that file compares byte for byte with the original file.

I remove the drive and stick it in a raspberry pi and RetroPi boots up instead of RasPlex, the data that was originally on the flash drive.  Nothing has been written to the SD card.

I'm stumped.  I've used dd to write various types of disk images and it has almost always worked fine over the years.  I don't care to use windows programs to write these drives.  I've always used dd.

---

### Post by kerry_s on 2018-05-14
see what it looks like in the disks app, you can also use that to write/restore image to the usb.

---

### Post by dpg1 on 2018-08-07
Thanks for the advice folks and your patience with my reply.   I rebuilt both my work and home desktops in the same week, one from Windows 7, and the other from Ubuntu Xenial.  I was quite harried in getting back to productivity and this problem got pushed to the bottom of the stack.

So perhaps there was a clue to my problem in what image was on my usb drive.  This disk came from a Raspberry Pi system, and my current theory is that that disk was trashed by too many writes, or some other problem.   

I did cycle back and tried 'disks' and it was just as flaky as using the old guard CLI commands.  I would delete the partition and it simply would not delete.

At least disks would give me a cryptic error message when I tried to format it and it would fail.    It was a good 32GB Sandisk Ultra so I am sad at my loss, but I have accepted that the disk is bad.

I put a different MicroSD in and was able to format it and copy images just fine.

---

### Post by HermanAB on 2018-08-08
Well, you were assuming that it is /dev/sdc and as the saying goes, assume makes an ass of u and me...

Since it is a removable, disk, it can be sdd or sde...

You should check it in /dev:
$ ls /dev/sd*

You should also check with dmesg after plugging the thing in.

---

