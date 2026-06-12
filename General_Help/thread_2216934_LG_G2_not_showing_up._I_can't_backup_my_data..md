---
title: "LG G2 not showing up. I can't backup my data."
date: 2014-04-14
forum: General Help
---

### Post by YQ002lc2 on 2014-04-14
I attach my LG G2 phone to my computer to rsync my data. 

At first, Lubuntu pops up the normal "Open folder to view files" prompt. 

I select the "Open folder to view files and it opens a verizon wireless section I've never seen before. 

I select MTP sync on my phone to connect it as a media device. 

Ordinarily, I would then see two more prompts to "Open folders to view files" but nothing else shows up and the verizon partition disappears.

This is what I get before and after I plugin the device:

Before: 
{
lubuntu@lubuntu:~$ sudo lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 08ff:2810 AuthenTec, Inc. AES2810
Bus 001 Device 004: ID 0c45:643f Microdia 
Bus 001 Device 003: ID 413c:8197 Dell Computer Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
lubuntu@lubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/cow            2.0G  1.5G  527M  74% /
udev            2.0G  8.0K  2.0G   1% /dev
tmpfs           393M  1.3M  392M   1% /run
/dev/sdb1       7.5G  696M  6.8G  10% /cdrom
/dev/loop0      638M  638M     0 100% /rofs
none            4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs           2.0G   36K  2.0G   1% /tmp
none            5.0M     0  5.0M   0% /run/lock
none            2.0G   80K  2.0G   1% /run/shm
none            100M   32K  100M   1% /run/user
/dev/sda3       465G   60G  406G  13% /media/lubuntu/OS
lubuntu@lubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x61fce6e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
Partition 1 does not start on physical sector boundary.
/dev/sda2   *       81920     1617919      768000    7  HPFS/NTFS/exFAT
/dev/sda3         1617920   976771071   487576576    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 8021 MB, 8021606400 bytes
247 heads, 62 sectors/track, 1023 cylinders, total 15667200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00007df1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62    15666221     7833080    c  W95 FAT32 (LBA)
lubuntu@lubuntu:~$ ls /dev/ | grep sd
sda
sda1
sda2
sda3
sdb
sdb1

}

After{
lubuntu@lubuntu:~$ sudo lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 08ff:2810 AuthenTec, Inc. AES2810
Bus 001 Device 004: ID 0c45:643f Microdia 
Bus 001 Device 003: ID 413c:8197 Dell Computer Corp. 
Bus 001 Device 041: ID 1004:621c LG Electronics, Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
lubuntu@lubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/cow            2.0G  1.5G  527M  74% /
udev            2.0G  8.0K  2.0G   1% /dev
tmpfs           393M  1.3M  392M   1% /run
/dev/sdb1       7.5G  696M  6.8G  10% /cdrom
/dev/loop0      638M  638M     0 100% /rofs
none            4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs           2.0G   36K  2.0G   1% /tmp
none            5.0M     0  5.0M   0% /run/lock
none            2.0G   80K  2.0G   1% /run/shm
none            100M   32K  100M   1% /run/user
/dev/sda3       465G   60G  406G  13% /media/lubuntu/OS
lubuntu@lubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x61fce6e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
Partition 1 does not start on physical sector boundary.
/dev/sda2   *       81920     1617919      768000    7  HPFS/NTFS/exFAT
/dev/sda3         1617920   976771071   487576576    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 8021 MB, 8021606400 bytes
247 heads, 62 sectors/track, 1023 cylinders, total 15667200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00007df1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62    15666221     7833080    c  W95 FAT32 (LBA)
lubuntu@lubuntu:~$ ls /dev/ | grep sd
sda
sda1
sda2
sda3
sdb
sdb1
}

---

### Post by YQ002lc2 on 2014-04-14
I should mention that I have two LG G2 phones. The same senario happens with both phones. 
Thank you.

---

### Post by YQ002lc2 on 2014-04-14
After hours of troubleshooting, I plugged in my older LGG2 phone.  All of the sudden I could access the files.

It seems that the phone I plug in last is the one that shows up.

I have no explanation for this behavior.

I will say that I am using a Lubuntu 13.10 live USB and that I've been having a similar issue accessing external hard drives with this image.

---

