---
title: "NDAS partition wiped after power failure"
date: 2008-03-14
forum: General Help
---

### Post by diskace on 2008-03-14
Hi all, this is an interesting story.

I have an NDAS external hard drive that i access from ethernet port. The drive was running fine for months until my APC backUPS died and created a power problem.

I suspect that the NDAS drive didn't liked that.

Here is my problem, when i try to mount the NDAS drive again the partition table is wiped totally.

I decided to connect the disk in usb rather than using ethernet and did

cfdisk /dev/sdb

to check partition table that i already created (ext3)

None.... everything disappeared.

Any idea what i can do ?

Thanks

---

