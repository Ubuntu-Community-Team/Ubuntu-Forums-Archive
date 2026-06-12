---
title: "Format unallocated space between windows and ubuntu partitions"
date: 2015-11-22
forum: General Help
---

### Post by philk949 on 2015-11-22
Hi,
I'm running a dual boot system with Windows 10 (350Gb sda2)and Ubuntu Mate 15.1 (79Gb sda3). Between these two partitions is a block of unallocated space I would like to reclaim if possible, by formatting it to an ext4fs and extending the Ubuntu partition. So far I've used Gparted without success.
Could you tell me how and if this can be done please. Thank you.

---

### Post by Hodevah on 2015-11-22
have you done this through a live CD? partitions, most especially linux/gnu partitions need to be unmounted. 
YOu can install gparted to a live cd and control your partition through that method. 
Forget trying to do this through Windows if you did, that is. Won't work
Partition needs to be unmounted. Hence live cd. 
Easy method and very safe to do.

---

### Post by philk949 on 2015-11-22
Thanks Hodevah,
Initially I tried with a live CD with gparted pre-installed then installed gparted to my OS and tried from there. Still couldn't do it. No, didn't try in Windows.
I'll try the live cd option again.

---

### Post by Bucky Ball on 2015-11-22
You MUST resize the / partition from Live media. You don't need to create a partition in the free space. Why? That would block the Ubuntu partition from expanding. :)

Boot from the Live media> Launch Gparted> right click the Ubuntu partition and make sure it is unmounted> right click and 'Resize'. Expand the partition into the free space. That's it.

If this is still an issue, please provide a screenshot from Gparted.

---

### Post by philk949 on 2015-11-22
Thanks mate. I'll give it another shot.

---

### Post by tokyobadger on 2015-11-22
SSD or HDD?
Show us the output of
```
sudo fdisk -l
```

---

### Post by Bucky Ball on 2015-11-22
*Thread moved to **General Help**.*

> Thanks mate. I'll give it another shot. 

Please do and let us know how you go (and a hello from sunny Adelaide!). :)

---

### Post by Phil_Anthony on 2015-11-22
This is the terminal output requested (sudo fdisk -l)

ubuntu-mate@ubuntu-mate:~$ sudo fdisk -l

Disk /dev/loop0: 1 GiB, 1088700416 bytes, 2126368 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xe01cc196

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048    407551    405504   198M  7 HPFS/NTFS/exFAT
/dev/sda2          407552 809367551 808960000 385.8G  7 HPFS/NTFS/exFAT
/dev/sda3       817498112 974749695 157251584    75G 83 Linux
/dev/sda4       974749696 975777791   1028096   502M 27 Hidden NTFS WinRE

---

### Post by Phil_Anthony on 2015-11-22
Thanks everyone, all done. Rebooting system now from dual boot hard drive to make sure the Os are behaving themselves. If there are tears I'll be back.
And a hello right back atcha from the sunny Gold Coast, Bucky Ball.

---

