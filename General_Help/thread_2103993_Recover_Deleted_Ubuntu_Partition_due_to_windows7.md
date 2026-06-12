---
title: "Recover Deleted Ubuntu Partition due to windows7"
date: 2013-01-11
forum: General Help
---

### Post by shrawat on 2013-01-11
Hi All.

I have a dual boot machine which initially came with  windows 7 and i installed ubuntu 12.04 on it. For an year i have been  working on ubuntu without having to boot into windows even once. Though  when i did boot in yesterday it seem to have corrupted the partition  table for the Ubuntu partition .  

I tried booting up using the live cd and this is what it shows.

[HTML]
ubuntu@ubuntu:~$ sudo fdisk -lu 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0a80af44

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    30410751    15204352   27  Hidden NTFS WinRE
/dev/sda2   *    30410752    30615551      102400    7  HPFS/NTFS/exFAT
/dev/sda3        30615552   879611670   424498059+   7  HPFS/NTFS/exFAT
/dev/sda4       879611902  1953523711   536955905    5  Extended
/dev/sda5      1935702016  1953523711     8910848   82  Linux swap / Solaris

Disk /dev/sdd: 8032 MB, 8032092160 bytes
131 heads, 50 sectors/track, 2395 cylinders, total 15687680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        8192    15687679     7839744    b  W95 FAT32

[/HTML]

My linux partition is being shown to be unallocated. 
Based on previous posts on the forum i tried to fix it using "testdisk"
Output from the testdisk are attached. 

I  currently need help on how to proceed further which guarantees me not  loosing any data or doing something wrong which i might not be able to  recover from. 

Appreciate if someone experienced with "test disk" can guide me here. 

My current thought is to change Linux partition from "D" to "L" (as it doesnt allow me to make it P)
Is there a way i can take a back up of my data, even if the linux installation itself can not be recovered.

Regards

---

### Post by oldfred on 2013-01-11
It looks like it has to be L or logical as it is inside your extended partition. 

IF all else fails, part of testdisk is photorec. It does a low level scan of a drive looking for anything that looks like a file. Since file table is gone, you do not get filenames, just extensions by file types and it takes a very long time. Plus you have to have room on another drive to copy recovered data to.

Also instructions on imaging drive as backup.
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

---

