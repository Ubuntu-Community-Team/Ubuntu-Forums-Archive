---
title: "CD in DVD drive sometimes not detected"
date: 2014-12-25
forum: General Help
---

### Post by pouldney on 2014-12-25
I have an acer  Aspire-AXC-605-ER30 Desktop with ubuntu 12.04
  Sometimes my CD in the DVD drive is detected and sometimes not.
    If it is not detected, I have to re-boot and it may then
 be detected.
       When it is not detected it does not appear in lshw ,sudo blkid
  or in hwinfo --block --short

---

### Post by Dawson_Harrison on 2014-12-25
Is it a certain type of CD that this happens with? Or is it every one.....

---

### Post by coldraven on 2014-12-26
Try cleaning the lens before you seek software solutions.

---

### Post by pouldney on 2014-12-28
The disk drive works well in Windows 8 , So it is probably a software problem in ubuntu

---

### Post by silverslimer on 2014-12-30
Cleaning the lens? Really? Is there any less helpful advice than that? This is a bug in Ubuntu and there's nothing more to it. It's up to the developers to acknowledge it and fix it. No amount of "works for me, must be you" will make this problem go away for users.

---

### Post by CharlesA on 2014-12-30
> **silverslimer said:**
> Cleaning the lens? Really? Is there any less helpful advice than that? This is a bug in Ubuntu and there's nothing more to it. It's up to the developers to acknowledge it and fix it. No amount of "works for me, must be you" will make this problem go away for users.

The developers don't visit the forums. A bug could be reported on Launchpad, but that is pointless because there is no information from the OP: DVD Drive type, model, lshw results, etc. If it's a normal SATA drive, there should be little reason why it doesn't work in Ubuntu as the drivers for that type of device are baked into the kernel.

---

### Post by pouldney on 2014-12-31
I did some more investigation on this problem.
I noticed that the cd was not detected on the first boot of the day.
So this morning I booted first in Windows8 ,and the disk was
not detected in windows!!
So now it seems it is a cd/dvd drive problem,Perhaps it needs to
"warm up"

---

### Post by pqwoerituytrueiwoq on 2014-12-31
check if the sata or ribbon cable is plugged in all the way
open the disk drive and use some canned air on it
replacement optical drives run 10-20 on newegg

---

### Post by Penguin360 on 2014-12-31
Is this a CD you burned yourself? I found that the high burn speed sometimes results in a unreadable CD for some old CD/DVD drive, so I usually choose low burn speed, like 4X or 8X.

---

### Post by pouldney on 2015-12-20
I still have this problem after updating to ubuntu 14.04
It seems if I boot with a CD in the drive it is detected but if I insert a CD
after boot it will not detect the cd or the drive

---

