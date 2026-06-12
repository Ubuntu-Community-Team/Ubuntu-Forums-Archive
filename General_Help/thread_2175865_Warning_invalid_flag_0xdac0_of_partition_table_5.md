---
title: "Warning: invalid flag 0xdac0 of partition table 5"
date: 2013-09-21
forum: General Help
---

### Post by patslap on 2013-09-21
I have a dual boot laptop with Win7 and Ubuntu 12.10.

Win7 had Truecrypt and was encrypted. I unencrypted the drive whilst in windows, rebooted, and machine boots straight into windows with no GRUB menu.

I've run a live Ubuntu disk and followed some other solutions, but can't seem to fix the partition flag problem so that I can boot into Ubuntu (after choosing it in GRUB) .

fdisk -l displays

```
ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# fdisk -l
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0xdac0 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb8fa9e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    37750783    18874368   27  Hidden NTFS WinRE
/dev/sda2   *    37750784    37955583      102400    7  HPFS/NTFS/exFAT
/dev/sda3        37955584   533023897   247534157    7  HPFS/NTFS/exFAT
/dev/sda4       533024766   976771071   221873153    5  Extended
/dev/sda5   ?  2051268866  3316957554   632844344+  5a  Unknown
```

Can anyone help? I don't want to lose data on Ubuntu drive if at all possible.

Many thanks

---

### Post by oldfred on 2013-09-22
What does testdisk show? 
Windows often corrupts extended/logical partition table entries as it does not see Linux partitions correctly.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)

 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

