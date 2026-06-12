---
title: "HD errors / Partition 2 does not start on physical sector boundary"
date: 2014-08-31
forum: General Help
---

### Post by russ3 on 2014-08-31
I've been having some hard drive issues - I believe they're caused by a power issue - i live in an old apartment building - and a lot of people are running ACs in the summer - so occasionally the lights will dim/etc.  The problem is that while I'm using Ubuntu 12.04 - I will suddenly lose all read/write privileges (all the the folders have locks next to them) - and the system will not reboot.  Using the Ubuntu boot disk, the drive won't even be able to be mounted.  But using FSCK on the main partition will solve that problem, and the system is bootable again - this happened a couple weeks ago, and the system worked fine, until it happened again.  This time I can again solve the problem and reboot - but almost immediately after logging in, I get an I/O error about my cache.  Everything runs real slow as well.  I am wondering if the way my partitions are set up is causing this problem.  Fdisk gives me the error in the title - and it looks strange that sda2 and sda5 are using the same space.  Any ideas what is going on here?  Not real experienced.  Here is the complete output from fdisk.  I had a similar problem around the same time last year , except didn't get the cache error when I started using the system again.  

Disk /dev/sda: 2000.4 GB, 2000397852160 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907027055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00003767

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  3891300351  1945649152   83  Linux
/dev/sda2      3891302398  3907024895     7861249    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5      3891302400  3907024895     7861248   82  Linux swap / Solaris

---

### Post by yancek on 2014-08-31
The error in your title is pretty common and should not affect the operation of the computer.  I see it all the time on working computers so something else is probably happening.  Having unreliable power isn't a good thing and there is nothing your operating system can do about that. 

The other part of your question is not a problem at all.  sda2 is a primary partition being used as an Extended partition and inside the Extended you have the swap partition.  You have used all the space for the Extended as swap, nothing unusual or problematic about that.

---

### Post by russ3 on 2014-08-31
Thanks for letting me know that the subject title isn't an issue.  Installed a ton of updates, and the problem seems to have gone away.  Did run Disk Utility which shows the drive has 11 bad sectors.  If anything I'd put the blame on the motherboard / SATA ports - I've noticed that sometimes when I run into a major problem, switching which SATA port I'm using seems to help - but none of the ports seem to be consistently bad.  Pretty low on cash right now, so I guess I have to deal with it.

---

### Post by yancek on 2014-08-31
You might trying doing a filesystem check.  How to do that and what it does is explained at the link below.

[http://askubuntu.com/questions/299483/how-to-clear-bad-sectors-in-hard-disk-using-ubuntu](http://askubuntu.com/questions/299483/how-to-clear-bad-sectors-in-hard-disk-using-ubuntu)

---

### Post by russ3 on 2014-08-31
I ran FSCK plenty of times when the drive was unmountable, it now says the file system has no errors.  That link actually says that fsck is unable to do anything about physically bad sectors on the drive.  At least I only have 11 bad sectors, instead of the 1200 the guy in that link had!

---

### Post by russ3 on 2014-09-01
Used Disc Utility, ran a SMART self-check on the drive, it fails almost immediately - and tried switching SATA cables and SATA ports with the same result.  Guess I'm gonna be getting a new HD soon, seems like this one is a timebomb, unless anyone else has any ideas.

---

### Post by yancek on 2014-09-01
> That link actually says that fsck is unable to do anything about physically bad sectors on the drive

Right but, what it does is label them so your system doesn't try to use them resulting in the errors.

---

### Post by russ3 on 2014-09-01
I'm actually looking at the SMART data for the drive now - the "current pending sectors count" is actually decreasing - from 13, 11 to 10.  These haven't been remapped, they've been read or written to successfully.  System running nice and smooth too.  I know getting a new HD and at least making a backup is the smart idea...but my wallet's not liking the smart idea.

---

### Post by yancek on 2014-09-01
> .but my wallet's not liking the smart idea

The wallet always knows what is best.

---

