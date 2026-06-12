---
title: "Kernel panic after HDD problems."
date: 2008-03-24
forum: General Help
---

### Post by Everheart on 2008-03-24
Hi,

I have this problem that when I boot ubuntu 7.10, it kernel panics.
The error I'm getting is 'run-init: /sbin/init: not a directory. kernel-panic-not syncing'

I have 2 partitions on my HD, and the problem started on the windows partition (duh). I was trying to resize the windows partition with partition magic, but it said there were too many errors on the disk, so I fixed the bad sectors, which went fine until I suddenly got a BSoD.
Luckily I still had ubuntu but after a while I got bad sectors on that part of the HD too, resulting in grub boot error 17. I fixed those bad sectors too with a live CD, but now when I try to boot to ubuntu it kernel panics.
I tried to fix my HD with testdisk, but it says it can't recover the partition, although I can access the data from my linux partition just fine through live CD.
I managed to fix the windows partition through a whole night of chkdsking, so I can boot again into windows, but the linux partition still gives the kernel panic.
And I started really hating windows, so any help is greatly appreciated, so I can finally completely move over to ubuntu.

I don't know much about linux in general, but I can post logs or whatever other information that can be useful to solve this problem.

Thanks in advance,
Eli

---

### Post by nsche on 2008-03-28
I would boot from the live cd and fsck the disk.  Basicly the same thing you did with windows.  It should be no problem to access the partitions from the live cd version just make sure you pick the first one.

You should be able to do the following in a terminal (xterm or something like that) window:

[FONT="Courier New"]sudo fdisk -l /dev/sda[/FONT]
[FONT="Courier New"]sudo fsck /dev/sdaX[/FONT] where X is the partition you have problems with

Good luck
Norm

---

