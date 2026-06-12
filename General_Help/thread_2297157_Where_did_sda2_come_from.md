---
title: "Where did sda2 come from ?"
date: 2015-10-01
forum: General Help
---

### Post by bizhat on 2015-10-01
I have 3 HDD in my PC. Here is list of partitions on my PC

```

root@fwhlin:/mnt# parted -l
Model: ATA WDC WD20EZRX-00D (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  2000GB  2000GB  primary


Model: ATA ST31000528AS (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  262GB   262GB   primary   ntfs            boot
 2      262GB   528GB   265GB   primary   ntfs
 4      528GB   799GB   271GB   extended
 5      528GB   793GB   265GB   logical   ext4
 6      793GB   799GB   6433MB  logical   linux-swap(v1)
 3      799GB   1000GB  201GB   primary


Model: ATA WDC WD20EZRX-00D (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      17.4kB  3049kB  3032kB                     bios_grub
 2      3049kB  200GB   200GB   ext4
 3      200GB   2000GB  1800GB  ext4


root@fwhlin:/mnt#

```


As you can see /dev/sda have only one partition.

But mount and df shows i have /dev/sda2 mounted

```

root@fwhlin:/mnt# mount | grep "/dev/sd"
/dev/sdb5 on / type ext4 (rw,errors=remount-ro)
/dev/sda1 on /mnt/drive_d type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda2 on /mnt/backup_win type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc3 on /home/boby/disks/part_data type ext4 (rw,nosuid,nodev,_netdev)
root@fwhlin:/mnt# df -h | grep "/dev/sd"
/dev/sdb5       243G  189G   42G  82% /
/dev/sda1       928G  669G  260G  73% /mnt/drive_d
/dev/sda2       928G  697G  232G  76% /mnt/backup_win
/dev/sdc3       1.7T   61G  1.5T   4% /home/boby/disks/part_data
root@fwhlin:/mnt# 

```

These two file systems have different files too (i verified)

```

root@fwhlin:/mnt# ls -l /mnt/drive_d | wc -l
11
root@fwhlin:/mnt# ls -l /mnt/backup_win/ | wc -l
28
root@fwhlin:/mnt# 

```

I forget how it looked in my windows, it was dual boot, was a windows user, but now my windows not working, its ok as i am full time ubuntu now.

I tried fdisk too, it also shows similar to parted -l, one partition on /dev/sda

Any idea where /dev/sda2 come from ?

---

### Post by bizhat on 2015-10-01
I checked with Disks, that shows 2 partition on /dev/sda, why parted and fdisk fail to show this ?

[IMG]http://i.imgur.com/GI5llFM.png[/IMG]

```

root@fwhlin:~# parted /dev/sda print
Model: ATA WDC WD20EZRX-00D (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  2000GB  2000GB  primary

root@fwhlin:~# fdisk -l /dev/sda

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x4df2bfef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63  3907027119  1953513528+  42  SFS
Partition 1 does not start on physical sector boundary.
root@fwhlin:~# 

```

---

