---
title: "Recovering data from LVM on RAID"
date: 2006-11-28
forum: General Help
---

### Post by daijavad on 2006-11-28
I had two disks (2x250GB) with RAID1 (Linux software raid) on, and LVM on top of this.

I was intending to replace this set with a set of 2x120 disks instead, and using the 2x250 disks as in a LVM volume group ("RAID0"/spanning/jbod/whatever).

I started with setting up a new RAID1 with LVM on the 2x120 disks, pretty straightforward. Then I broke up the 2x250 array, destroyed all partitions on one of the disks, and made a new volume group and added this disk to it.
Then I copied roughly half of the data (the important data) over to the volume group of the 2x120 RAID1. The other half went to the unimportant volume group with the now just one 250GB disk. After this was done, and I was pretty confident that all files had been copied (90% sure), I finally removed the remaining bits of the 2x250 GB disk array, and destroyed all partitions on the other 250 GB disk as well. I was about to add this as a physical volume to LVM (pvcreate), but it would not let me (insisting that the drive was busy, despite trying the usual tricks to "release" it). Ok, so I rebooted, and pvcreate worked fine.

It is now that I discovered that roughly half of my "important" folders were gone (in somewhat random order)! I was, as I said, 90% sure that I had copied everything.

So here we are, at the core of the problem; how to recover the files?
If you have any experience in this field, or any pointers, suggestions et.c. that can help me solve this problem, I would greatly appreciate it.

I have tried a few tools, the free linux recovery tool from r-tt.com, as well as their full version (demo). I have also tried PhotoRecovery and OnTracks EasyRecovery. These programs just leave me with thousands of files, mostly with a "default extension", and some that the programs guess are various files. When I look into the files, they also seldom start and end where you would think (i.e. they contain fragments of XML/jpg and other information...). R-tt's tool even suggested I had hundreds of ext2 partitions. I guess these results are logical consequences of using LVM, since LVM works with PE's scattered around the disk.

---

