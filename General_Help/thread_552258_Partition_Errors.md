---
title: "Partition Errors"
date: 2007-09-16
forum: General Help
---

### Post by Dramaman on 2007-09-16
I'm running Feisty on a Dell Inspiron 6000 with a 60 gig EIDE drive.  In the last two weeks I've had two instances where my boot-up was interrupted because of a fsck problem that dropped me to a command line.  In both cases, the complaint was about a "bad magic number in superblock while trying to open /dev/<device>."  They were different partitions in each instance.

The partitions are all ext3 and when executing a simple 'fsck.ext3 /dev/<device>' everything seemed to check out fine.

When the second occurrence happened I researched online to determine the proper alternative superblocks to find.  I read that I could find them using dumpe2fs.  Doing so I tried 'fsck.ext3 -b 32768 /dev/sda9'.  This worked and found several problems during "Pass 5: Checking group summary information."  I selected that each problem be fixed and fsck.ext3 ended reporting that the corrections had been made.  However, running 'fsck.ext3 -b 32768 /dev/sda9' again causes the same errors to be reported.  No matter how many times I run the filecheck and agree to correct the errors, the problems still show up.

The errors that are being reported are:

Free blocks count wrong for group #0 (23948, counted=363).
Fix<y>? yes

Free blocks count wrong for group #1 (32156, counted=1).
Fix<y>? yes

Free blocks count wrong for group #2 (32253, counted=16).
Fix<y>? yes

Free blocks count wrong for group #3 (32156, counted=1).
Fix<y>? yes

Free blocks count wrong for group #4 (32253, counted=20012).
Fix<y>? yes

and so on...

What I'm wondering is whether this is an early sign that something is wrong with my hard drive, or whether it is something wrong with my partitions that can be fixed?

At this point the only thing I can think of doing is an entire backup, deleting all my partitions, recreating them and then reloading.  I'd like to avoid the hassle if possible.

---

### Post by JinxAu on 2007-09-16
Gday Dramaman,

You may have better results by booting to a Ubuntu Live environment using the Desktop CD/DVD and running the commands from there. My understanding is you can not edit a fileystem that is currently mounted.

Does seem like the drive needs  a bit of attention. Maybe try running the Dell diagnostics on the HDD to check to see if it is failing (usually available from BIOS when you boot).

Cya round
Jinx

---

### Post by Dramaman on 2007-09-17
I did run the fsck commands with the partitions unmounted, using a usb linux distro (SLAX). I got the same results.  I went ahead and backed up everything, just to be safe.  I'll check the BIOS for the HD checking utility that you mentioned.

---

