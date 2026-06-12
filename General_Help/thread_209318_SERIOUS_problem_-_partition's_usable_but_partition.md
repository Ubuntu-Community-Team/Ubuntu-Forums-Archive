---
title: "SERIOUS problem - partition's usable but partitioning table destroyed!"
date: 2006-07-04
forum: General Help
---

### Post by clintonthegeek on 2006-07-04
Hi everyone,

I'm posting this from Kubuntu, running off of hda1 on my hard drive. However, an installation of Windows 98 onto the unallocated space (1.5gb) on my hard drive has totally messed up my partitioning!

Everything works for now, but I can't view or change any of my partition info. fdisk won't open, it just says 
```
clinton@clintonubuntu:~$ sudo fdisk hda
Password:

Unable to open hda

```

When I try to load hda in the GParted Live! CD to edit it it shows all 80gb as unallocated and empty! Does the same running it off the hard drive.

QTParted from my Kubuntu installation says "Critical error during ped_disk_new!" when I try to view /dev/hda's partition info.

What I did was repartition my hard drive to have 1.5 gig of unallocated space (the Windows 98 install CD wasn't recognizing the fat16/32 partitions I made from linux), and use 98's fdisk to make a new fat32 partition in the unallocated space. I then formatted it in Kubuntu using "makefs.vfat -F 32 /dev/hda3", restarted with the 98 cd and installed it. It naturally screwed up my MBR, which I fixed again with a Damn Small Linux CD.

Everything works *for the moment*. But, how can I fix my partition table, especially if all the programs that work with partitions CAN'T EVEN SEE THEM?

Any help is appreciated!

-Clinton

EDIT: Wait... everythigns is NOT working great... Windows 98 won't even boot! argh!

And, when I run KDiskFree, it tells me that hda1 (Kubuntu) is 71.2gb big (okay), and that hda3 (98) is 66.7gb large (!) which is impossible because I only have an 80gb hard drive! hda3 is 1.5 gb large.

---

### Post by Arisna on 2006-07-05
This doesn't look to me like it will be easy to fix, but I did notice that you would need to use ```
sudo fdisk **/dev/**hda
``` for the command line fdisk to give you a more useful error message/to actually work.

---

### Post by clintonthegeek on 2006-07-05
OMG... good point. :p

But, no worries because I FIXED IT! yeay!

Doing some googling on partition tables, I found TestDisk, a command-line utility to fix corrupted partition tables. One "sudo apt-get install testdisk" later it ran through my hard drive, found the last two partitions (my swap partition and the 98 partition) overlapping, and wrote me a new one.

Thanks for the quick response! :D

-Clinton

---

