---
title: "Drive recognized as wrong FS type"
date: 2008-03-29
forum: General Help
---

### Post by apollyon0810 on 2008-03-29
So I have 3 hard drives in my computer.

The two of importance are sdd and sde

sdd is a 150GB raptor with 3 partitions.  100gb to Windows, 45gb to Ubuntu, and 5gb for the swap partition.

Everything seems to be fine with /dev/sdd, but /dev/sde is now recognized as a linux swap partition.  The WHOLE DRIVE.  It's 500gb's.  I'm pretty sure that Linux is using the swap partition that I created for it (the 5gb on sdd), and hasn't touched my 500gb hard drive.  What I want to know is if there is any way of changing my 500GB hard drive back to NTFS without loosing all the data on it.  It's literally years worth of TV shows, MP3's, personal pics of family and stuff.  Pretty important data (to me) that I don't want to loose.

I was thinking about just "fdisk /dev/sde/ and changing the FS type back to HPFS/NTFS...  but i wanted to see if anybody else had any good suggestions first.

Thanks for your help in advance.

---

### Post by apollyon0810 on 2008-03-29
matthew@matthew-desktop:~$ sudo fdisk -l

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00080e21

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12158    97656250    7  HPFS/NTFS
/dev/sda2           12159       12766     4883760   82  Linux swap / Solaris
/dev/sda3           12767       18241    43977937+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3df7b554

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60802   488384512   82  Linux swap / Solaris

Disk /dev/sdc: 2024 MB, 2024275968 bytes
255 heads, 63 sectors/track, 246 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69460dd6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         247     1976768    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(245, 254, 63) logical=(246, 26, 36)


/dev/sdc is a 2gb thumb drive I have plugged in.  But you can see my problem with /dev/sdb.  /dev/sda is set up exactly how I want it though.

---

