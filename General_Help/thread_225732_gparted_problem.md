---
title: "gparted problem"
date: 2006-07-30
forum: General Help
---

### Post by myha on 2006-07-30
Hi all,

I am having problems with gparted (or disk maybe...?)

When I run it I see only unallocated disk space, like the disk is completely empty. I tried to run gparted livecd also and same story there...

Does anyone have any idea of where the problem could be?

regards

---

### Post by zxee on 2006-07-30
I don't know why gparted isn't seeing all of your partition. I have found gparted to be quirky though. You could use cfdisk. The way to use cfdisk is from a terminal/shell > cfdisk /dev/hdXreplace the X with the letter that designates your drive; a,b....
Hope that helps.

---

### Post by myha on 2006-07-30
Hi,

I tried cfdisk and here is the output that I get...
```
 FATAL ERROR: Bad logical partition 6: logical partitions overlap
```

I think that the partition layout is somehow damaged....

---

### Post by zxee on 2006-07-30
It would appear so. Perhaps the drive is failing? I don't know, but you can also try fdisk (takes the same arguments as cfdisk) if that gives a similar output you may need to reformat or replace the drive.
To determine whether or not this is a drive failing situation you may want to read and implement this: [http://smartlinux.sourceforge.net/smart/](http://smartlinux.sourceforge.net/smart/)

---

### Post by myha on 2006-07-31
Hi,

I am pretty sure that this is not a drive issue, I ran partition magic and it said that start of one partition is overlapping with another, so I think that this is a partition layout problem. I don't have any problems either that would point to disk problem.

The problem is that this is work computer, and I cannot reinstall windows alone because of domain access and company policy - uffortunately I need windows for remote access through RSA (As far as I know this could be solved via openswan, but I haven't got it working yet).

Thank you anyway, I will figure something out.

regards

---

