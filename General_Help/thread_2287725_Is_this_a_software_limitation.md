---
title: "Is this a software limitation?"
date: 2015-07-21
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2015-07-21
i recently got a 2TB HDD and put a GPT partition table on it (w/ gparted), but the gnome disk utility does not see that
[[IMG]http://i.imgur.com/KalE9vrl.png[/IMG]]("http://i.imgur.com/KalE9vr.png")
my 500GB drive shows GUID partition table, but my 2TB drive shows unknown, kinda wondering why
```
~$ sudo fdisk -l
[sudo] password for chad: 

Disk /dev/sda: 30.0 GB, 30016659456 bytes
255 heads, 63 sectors/track, 3649 cylinders, total 58626288 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ef58a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    40964095    20481024   83  Linux

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1   976773167   488386583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  3907029167  1953514583+  ee  GPT
Partition 1 does not start on physical sector boundary.

```
```
[sudo] password for chad: 
Model: ATA Corsair Nova 2 S (scsi)
Disk /dev/sda: 30.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  21.0GB  21.0GB  primary  ext4         boot


Model: ATA WDC WD5000AAKX-0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      17.4kB  2681MB  2681MB  ext4
 2      2681MB  250GB   247GB   ext4
 3      250GB   252GB   1612MB  ext4
 4      252GB   500GB   248GB   ext4


Model: ATA ST2000DM001-9YN1 (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 3      17.4kB  1865GB  1865GB  ext4
 2      1865GB  1988GB  122GB   ext4
 1      1988GB  2000GB  12.9GB  linux-swap(v1)
```

---

### Post by oldos2er on 2015-07-21
Do you have the *gdisk* package installed?

---

### Post by pqwoerituytrueiwoq on 2015-07-21
looks like i do
```
apt-cache policy gdisk
gdisk:
  Installed: 0.8.8-1ubuntu0.1
  Candidate: 0.8.8-1ubuntu0.1
  Version table:
 *** 0.8.8-1ubuntu0.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     0.8.8-1build1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

```

---

