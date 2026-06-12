---
title: "Windows does not boot after 8.04 install"
date: 2008-06-15
forum: General Help
---

### Post by posey on 2008-06-15
I have a Foxconn Nf4sli7aa board, with a Pentium 4 Prescott 3.0Ghz processor, Geforce 6600 PCI-E video card, 1gb of ddr2 ram, a 320gb seagate sata hard drive, and an ide cdrom drive.

I just got the new board and am trying to rebuild the system to a functional state. It needs to dual boot Windows XP Pro and Ubuntu (the users favor Ubuntu over other linuxes). 

I formatted the drive, and installed XP in sda1, a 100gb partition. I beat on Windows for a while, updates, defrag, reboot after reboot after reboot. Windows worked well, booted every time, no problems.

Then I got out the Ubuntu 8.04 disc and booted it (first checking the disc for errors), and installed Ubuntu. I used manual partitioning and used the free space after sda1. Ubuntu has sda2 as /, a 100gb partition, and sda3 as a 2gb swap space (that will likely go largely unused). Ubuntu installed fine and grub made a correct menu.lst. Ubuntu boots fine, ran updates, installed the nvidia drivers, etc. 

The problem now is that Windows won't finish booting. When grub comes up and Windows XP is selected, XP starts to come up correctly and gets to the screen where it says "Windows XP" and has the bar that the blue squares run across. The blue squares will run across that bar, pausing every now and then, for as long as one wants to wait on them (20 minutes +). It never gets any farther. Safe mode does work, but I'm not convinced it works reliably. 

The settings in grub appear to be correct, and changing them to include root noverify or removing savedefaults does not change anything.

According to chkdsk /r and Norton Ghost, theres nothing wrong with the drive. Memtest86 doesn't find any problems with the ram. 

What happened and how can I fix it?

---

### Post by logos34 on 2008-06-15
> **posey said:**
> According to chkdsk /r and Norton Ghost, theres nothing wrong with the drive.

That's the first thing I would have tried.

Next, I'd try booting into the xp recovery console and running

**fixboot c:**

If that doesn't work either, try TestDisk to fix any problems with the partition table. Just be careful when writing any changes to disk.

Add:

you're windows entry in menu.lst is 'root (hd0,0)', no?

What's fdisk show?

sudo fdisk -l

---

### Post by posey on 2008-06-16
Using the windows recovery console, running fixboot did not change anything. Safe mode boots well and quickly, but normal mode still stays at the loading screen forever.
Windows isn't throwing any errors from trying to boot, the event log does not start.

I defragmented the crap out of the windows partition (in safe mode), for good measure, with no results (it was already in good shape). 

I didn't try testdisk, but fdisk is usually pretty good at saying "hey, problems with your partition table" and so is the windows recovery console. Neither reported any problems.

This is actually the second time I've seen this happen - windows not working after a ubuntu installation on a separate partition. The first time I thought the user had just destroyed windows and ubuntu was a handy thing to blame - but that time normal mode and safe mode both did not work.

The grub stuff looks fine, and does work - windows couldn't pretend to start booting if grub was messed up. 

fdisk -l
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa3b8a3b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       24906    97659135   83  Linux
/dev/sda3           24907       25149     1951897+  82  Linux swap / Solaris

```

/boot/grub/menu.lst (important parts only)
```

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=9c7293ee-8752-4897-9ff4-871ff021525a ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=9c7293ee-8752-4897-9ff4-871ff021525a ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by logos34 on 2008-06-16
> **posey said:**
> Using the windows recovery console, running fixboot did not change anything. Safe mode boots well and quickly, but normal mode still stays at the loading screen forever.
Windows isn't throwing any errors from trying to boot, the event log does not start.

I defragmented the crap out of the windows partition (in safe mode), for good measure, with no results (it was already in good shape). 

I didn't try testdisk, but fdisk is usually pretty good at saying "hey, problems with your partition table" and so is the windows recovery console. Neither reported any problems.

This is actually the second time I've seen this happen - windows not working after a ubuntu installation on a separate partition. The first time I thought the user had just destroyed windows and ubuntu was a handy thing to blame - but that time normal mode and safe mode both did not work.

The grub stuff looks fine, and does work - windows couldn't pretend to start booting if grub was messed up. 


yeah, I agree about grub, it's doing its part and chainloading XP...so the problem is definitely on the windows side.

It appears you've tried all the obvious things.  

What about the windows ['repair install']("http://www.michaelstevenstech.com/XPrepairinstall.htm") option?  You'll have to reapply updates, SP3, etc. so find a way to back that up (unless you have a really fast internet connection where download time is not an issue).

Either that or reinstall windows. (Either way you'll still need to [restore grub to the mbr]("http://ubuntuforums.org/showthread.php?t=224351"))

---

### Post by posey on 2008-06-16
I'd really like to know what happened, especially since this is the second time I've seen this. It looks like ubuntu touched something in the windows partition that it should not have, but I can't tell.

I was hoping to avoid reinstalling/repair installing windows, though it is a clean build, since I intentionally installed windows first to avoid messing around with rescuing grub.

---

### Post by logos34 on 2008-06-16
> **posey said:**
> I'd really like to know what happened,

I understand your frustration...It bugs me too when I can't figure out why something went wrong, even if I manage to fix it! 

You could search the XP support page for things to try.  But you're not getting any error messages, which makes it hard to nail down.

---

