---
title: "installed hard drive missing GB?"
date: 2008-06-04
forum: General Help
---

### Post by vashwood on 2008-06-04
So I just installed a new 1tb hard drive.  I used fdisk to give it one partition.  And then I formatted it w/ ext3.  There should be nothing on it but when I looked at the drive it says 877GB free of 924gb.  What happened to the rest?

---

### Post by Xiong Chiamiov on 2008-06-05
I wonder if it has something to do with [the discrepancy between df and du]("http://www.cyberciti.biz/tips/freebsd-why-command-df-and-du-reports-different-output.html").

---

### Post by vashwood on 2008-06-05
for the installed hard drive...

df -h 
/dev/sdb1             925G  200M  878G   1% /mnt/storage

fdisk -l 
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00066782

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

And there is nothing on the drive

---

### Post by ilrudie on 2008-06-05
> **vashwood said:**
> And there is nothing on the drive

Technically thats not correct.  Unless your formatted it using ZFS there are a bunch of inodes on the drive.  I'm really not sure how much space they should be taking up on a 1TB disk though.  It probably depends on the ext3 settings used.

---

### Post by vashwood on 2008-06-05
I installed gparted to take a look and its showing that I have 917gb free of 925gb.

---

