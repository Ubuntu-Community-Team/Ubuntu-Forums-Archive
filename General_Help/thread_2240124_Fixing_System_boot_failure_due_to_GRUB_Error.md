---
title: "Fixing System boot failure due to GRUB Error"
date: 2014-08-18
forum: General Help
---

### Post by venkat-330 on 2014-08-18
We have a Linux system, which unpredictably goes in to non bootable mode. Listed are the errors that usually occurs in the system.
  1 > GRUB RESUE
2 > INTIRAMFS
3 > INIT SCRIPT FAILURE
  Currently, we are looking out to point a reason for these errors.  To start, I have collected the hard disk information of **GRUB RESCUE** error machine
  It would be great, If someone points the root cause for these errors. What are the measures that should be taken to  avoid these errors.
  **FDISK information:**
  Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xc4bd0d2c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3395    27261952   83  Linux
/dev/sda2            3395       28631   202706944   83  Linux
/dev/sda3           28631       38902    82503680    5  Extended
/dev/sda5           28631       38641    80404480   83  Linux
/dev/sda6           38641       38902     2095104   83  Linux
  **parted information:**
  Expected info:

Model: ATA ST320LT012-9WS14 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      2097kB  27.9GB  27.9GB  primary   ext3            boot
 2      27.9GB  235GB   208GB   primary   ext3
 3      235GB   320GB   84.5GB  extended
 5      235GB   318GB   82.3GB  logical   ext3
 6      318GB   320GB   2145MB  logical   linux-swap(v1)

 Recieved info:
 Model: ATA ST9320325AS (scsi)
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  27.9GB  27.9GB  primary   ** EXT3 MISSING **                boot
 2      27.9GB  235GB   208GB   primary   ext3
 3      235GB   320GB   84.5GB  extended
 5      235GB   318GB   82.3GB  logical   ext3
 6      318GB   320GB   2145MB  logical   linux-swap(v1)
  case **GRUB RESCUE**     In this when we try to mount our SDA partiton
  mount /dev/sda /mnt/test  : It throws **Mount: you must specify filesystem type**

mount -t ext3 /dev/sda /mnt/test  : 
It throws **VFS: can't find ext3 filesystem on dev sda1**
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
   missing codepage or helper program, or other error
   In some cases useful info is found in syslog - try
   dmesg | tail  or so
  Partition creation script details:
  device="/dev/sda"
echo "Partition create process start for ${device}"
a=$(fdisk -l | grep ${device})
disk=`echo $a | awk '{print $3}' | sed 's/\:$//'`
if [[ "$disk" == 320* ]];then #For 320GB primary disk
    fdisk -u ${device} < hddSectorInfo.sh

    ###hdd Sector info###
    # n p 1 4096 54527999
    # n p 2 54530048 459943935
    # n e 3 459948032 624955391
    # n l 459952128 620761087
    # n l 620765184 624955391
    # a 1  w  q
    ####


fi
mkfs.ext3 -F ${device}1
mkfs.ext3 -F ${device}2
mkfs.ext3 -F ${device}5
mkswap ${device}6
swapon ${device}6
  Also. request some pointers on partition creation..
          1. Making /boot as separate partition is a must ??
  Request pointers in fixing issue:


adding smart info:

[http://pastebin.com/ktBBCtXe](http://pastebin.com/ktBBCtXe)

---

### Post by bizhat on 2014-08-18
> **venkat-330 said:**
> In this when we try to mount our SDA partiton
  mount /dev/sda /mnt/test  : It throws **Mount: you must specify filesystem type**


You need to specify number, like

```
mount /dev/sda1 /mnt/test
```

> **venkat-330 said:**
> 
[COLOR=#000000]1. Making /boot as separate partition is a must ??[/COLOR]


Partition for /boot is not required.
[COLOR=#000000]
INTIRAMFS/ [/COLOR][COLOR=#000000] INIT SCRIPT FAILURE error look like you have some thing wrong with / partition. Check your /etc/fstab and see if anything wrong with /

Booting with a live DVD will be easier than manually mounting each partition.

[/COLOR]

---

### Post by venkat-330 on 2014-08-18
Yup i tried the same with "SDA1" still same error..

Also, made the HDD as secondary drive and tried to mount ..I got the same error.

It is noted with parted -l command i get:

Number  Start   End     Size    Type      File system     Flags
**  1      1049kB  27.9GB  27.9GB  primary                 boot ---- (This ext3 boot -- where ext3 is missing) **
 2      27.9GB  235GB   208GB   primary   ext3
 3      235GB   320GB   84.5GB  extended
 5      235GB   318GB   82.3GB  logical   ext3
 6      318GB   320GB   2145MB  logical   linux-swap(v1)

---

### Post by oldfred on 2014-08-20
Best to make sure you align partitions with newer 4K drive like you have.
Why not ext4?

 First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

[http://wdc.custhelp.com/app/answers/detail/a_id/5655](http://wdc.custhelp.com/app/answers/detail/a_id/5655)

---

### Post by venkat-330 on 2014-08-27
> **oldfred said:**
> Best to make sure you align partitions with newer 4K drive like you have.
Why not ext4?

 First, understand that most partitioning tools have moved to a policy  of aligning partitions on 1 MiB (2048-sector) boundaries as a way of  improving performance with some types of arrays and some types of new  hard disks (those with 4096-byte physical sectors). See article by  srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

[http://wdc.custhelp.com/app/answers/detail/a_id/5655](http://wdc.custhelp.com/app/answers/detail/a_id/5655)

Thanks for the suggestion and information provided.
Is there reason that partition mis alignment will lead to system failure..I am not a get a data of that sort..

---

