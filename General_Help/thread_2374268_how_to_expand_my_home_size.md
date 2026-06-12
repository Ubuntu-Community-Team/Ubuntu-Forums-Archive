---
title: "how to expand my /home size"
date: 2017-10-14
forum: General Help
---

### Post by widon1104 on 2017-10-14
I want expand my /home size from one of my windows use space&#65292;how can I do it.

---

### Post by Impavidus on 2017-10-14
Make sure you have backups and be prepared to reinstall everything, as partitioning sometimes goes wrong.

Use Windows to defrag the Windows partition you want to shrink, use Windows tools to shrink it and reboot Windows a couple of times to allow it to run its checks. Run Ubuntu from a live disk and use gparted to expand your /home partition into the unallocated space that came available when you shrank the Windows partition. Note that the partition to be shrunk and the partition to be expanded must be adjacent, or you'll have to shift intermediate partitions. In that case it's often better to find some more creative solution. If you have MBR-partitioning, beware of the extended partition. You may have to shift unallocated space in or out of that one.

To give more detailed advice we need the details of the partition layout of your hard drive.

---

### Post by vanadium on 2017-10-14
Changing the partition sizes using gparted, run from a live CD. Start with an Ubuntu live CD, start up Gparted.

Depending on your current partition layout, you will or will not be able to easily change the size without deleting data. Enlarging a partition is a very quick process. Moving a partition, however, takes a lot of time (and practically may not always succeed successfully).

Eventually post your partitioning here, so we can take a look: post the output of "sudo fdisk -l" eventually combined with "mount" (to have a better idea of what the partitions are).

---

