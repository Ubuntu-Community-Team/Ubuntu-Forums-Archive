---
title: "Partitioning a new disc"
date: 2023-03-27
forum: General Help
---

### Post by Phil Binner on 2023-03-27
I just installed a new Seagate ST2000VM003 2Tb hard drive.  I used Disks to Format the entire area as Ext4.  It did not work in the same way as other disks I have formatted in that there does not seem to be a partition, just the entire area.  The format seemed to work, however, and I proceeded to copy data to it.  There is a problem, however, because it does not hold as much data as it should.  I am copying  three folders to it of 1.4TiB, 94.1Gib and 67.4GiB.  It ought to fit.

Before I return the disk I want to be sure that it is not my error in the way I have formatted it.  When I look at it on GParted I see a single partition of 1.82Tib, but that partition resides at /dev/stc.  When I formatted two other discs on this machine I had to add partitions to them before I could format them.  GParted shows them as residing at /dev/sda1 and /dev/sdb1.  Further, when I tried to use GPartedto remove the partition on the new disk and start again I was unable to do it.  Clicking the dustbin on the partition has no effect.  Similarly the Disks utility does not give me the option to add or remove partitions, as it does with the other disks.

Help would be appreciated.  Thank you.

---

### Post by Dennis N on 2023-03-27
You need to make a partition table before you can create partitions. In gparted:
Device > Create Partition Table > GPT
Then you can make the necessary partitions and format them.

---

### Post by Phil Binner on 2023-03-27
What should the partition table type be.  The default seems to be msdos.

---

### Post by oldfred on 2023-03-27
The only reason to use MBR(msdos) is if installing Windows in old BIOS mode on old system.
Microsoft has required UEFI with gpt partitioning since 2012.
External drives cannot have full Windows install, anyway, so use gpt.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR](https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR)

Gpt is also required for any drive over 2TB.

With larger drives & even my larger 256GB or more flash drives, I like to have a small ESP & / partition, just for emergency boot. But I still have backups & multiple repair flash drives and now an external SSD with is a lot faster than the flash drives.

---

### Post by Phil Binner on 2023-03-27
Thanks for the help.  I can sort it from here.

---

