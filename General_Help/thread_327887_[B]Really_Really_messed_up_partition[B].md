---
title: "[B]Really Really messed up partition[/B]"
date: 2006-12-29
forum: General Help
---

### Post by fokuslee on 2006-12-29
This is my output from fdisk -l

01. Disk /dev/sda: 203.9 GB, 203928109056 bytes
02. 255 heads, 63 sectors/track, 24792 cylinders
03. Units = cylinders of 16065 * 512 = 8225280 bytes
04. 
05.    Device Boot      Start         End      Blocks   Id  System
06. /dev/sda1               2        9061    72774450    f  W95 Ext'd (LBA)
07. /dev/sda2   *       10200       24792   117218272+   7  HPFS/NTFS
08. /dev/sda3            9062       10199     9140985   83  Linux
09. /dev/sda5               2        9008    72348696    7  HPFS/NTFS
10. /dev/sda6            9009        9061      425691   82  Linux swap / Solaris

2 questions, sda1 and sda5 are overlapping the same cylinders ?? WTheck is w95...blah?
and where is my sda5?? 

this maybe a stupid question but im a linux nub so bear with me

---

### Post by taurus on 2006-12-29
There is nothing wrong with your harddrive...  /dev/hda1 is an extended partition so the first logical partition, /dev/hda5, should be at the beginning of that extended partition.  Therefore, you have two logical partitions, /dev/hda5 & /dev/hda6.

---

### Post by fokuslee on 2006-12-29
thx for ur help also thx to harrisonyl on irc
learning new things every day : )

---

