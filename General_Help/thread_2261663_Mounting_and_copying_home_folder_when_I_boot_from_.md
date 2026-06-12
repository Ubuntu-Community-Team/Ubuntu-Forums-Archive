---
title: "Mounting and copying /home folder when I boot from a live CD"
date: 2015-01-20
forum: General Help
---

### Post by jdix123 on 2015-01-20
I broke my /boot partition and after a week or so of fiddling with it, its probably just time to copy the /home folder and reinstall.

So I poked around around and found some questions and threads, problem is that when I fdisk -l my /root partition "doesn't contain a valid partition table"

Am I just out of luck?

---

### Post by TheFu on 2015-01-20
Partition tables are stored at the HDD level, not per-partition. That isn't good if there is an issue.  It could be logical corruption, but I've never seen that on a good HDD.  Definitely get your daily backup religion, if you don't have that already.

Try this command:

**sudo fdisk -l**
If that works, you shouldn't need to worry, at least not any more than anyone else needs to worry about disk failures. It is better to have backup religion before you need it. Just look around these forums for all the people who lost data due to failed hardware, stupid mistakes, being hacked, or RAID who didn't have backups.  Backups can solve most computer data problems, not just the obvious ones.

---

### Post by Holger_Gehrke on 2015-01-20
Or you're not using MBR partitions but the newer / more modern GUID Partition Table. 'fdisk' can't read those, but 'parted' can. So before you despair, try 'parted -l' (without any device names, it's smart enough to find them itself)

---

### Post by TheFu on 2015-01-20
fdisk has been updated, so most versions support GPT in most recent distros.
However, I use parted myself for this stuff.

GPT has a backwards compatible to MBR partition table in the location that MBRs are normally stored. It is only when more than 4 primary partitions exist that there should be any issues reading it by the older tools. Also, GPT doesn't have extended or logical partitions - doesn't need them because 128 primary partitions in GPT should be enough for a while.

---

