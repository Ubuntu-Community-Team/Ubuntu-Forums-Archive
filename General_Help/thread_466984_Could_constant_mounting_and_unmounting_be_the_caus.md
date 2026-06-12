---
title: "Could constant mounting and unmounting be the cause of my data loss?"
date: 2007-06-07
forum: General Help
---

### Post by BarfBag on 2007-06-07
I used to have my partitions arranged like this.

hda1 - 30 GB, NTFS, Windows
hda2 - 80 GB, FAT32, Data Partition
hda3 - 29 GB, ex3, Ubuntu
*hda5 - 1 GB, swap

*For some reason, it skipped over hda4.

I had them arranged that way so I could easily access my data in both operating systems.

My Windows partition got a worm that none of my virus scanners could remove, so I was forced to back-up and reformat.  As I was backing up, I realized that about 1/3 of my files were corrupt.  At first, I thought it was the worm.  But how could it damage data on other partitions?  Could it be the constant mounting and unmounting (booting in and out of Ubuntu) that caused the data loss?  If so, what filesystem do you recommend that is safer with this kind of thing, and works in Windows as well?

---

### Post by carolinason on 2007-06-07
Mounting and unmounting a drive should not corrupt data.

Research the worm to see what the payload is. Then you can get a better idea if it's software or hardware related. 

Do a scan of the drive to see if you have sector damage. Usually the vendor has a free utility to diagnose failures.

---

