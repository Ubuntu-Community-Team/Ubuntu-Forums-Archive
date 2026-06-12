---
title: "Mounting a single drive from a failed Raid 1 NAS -  special device does no exist"
date: 2018-06-04
forum: General Help
---

### Post by bark01 on 2018-06-04
Hi,

I have a file from a failed Dlink NAS. I've been told by the dlink forum gurus that the NAS uses a linux file system so mounting the drive in linux live should allow me to copy data from it.

I've loaded the drive in test version of a windows recovery program and can see all the files and file structure is in place, but I'd need to spend 100 euros on the actual program to recover it that way.

I'm a complete novice with linux but this is where I'm at:

I've booted into linux live using Knoppix 8.2

The Raid hard drive is connected via a USB drive (I could plug it in via internal sata if it made any difference) 

In the 'disks' program I can see the 3tb raid drive split into 4 partitions but the main data partition doesn't give me the option to mount
screenshots of 'disk' program: [https://imgur.com/a/kFaEZkz](https://imgur.com/a/kFaEZkz)

I'm now using LXTerminal to try and mount 

This is the result of fdisk -l
(The drive at the bottom is the one I'm trying to mount)

```
knoppix@Microknoppix:~$ fdisk -l
Disk /dev/ram0: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram1: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram2: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram3: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram4: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram5: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram6: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram7: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram8: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram9: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram10: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram11: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram12: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram13: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram14: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram15: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/cloop0: 9.7 GiB, 10439098368 bytes, 20388864 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/cloop1: 1.3 GiB, 1345585152 bytes, 2628096 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/zram0: 4 GiB, 4294967296 bytes, 1048576 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/sda: 477 GiB, 512110190592 bytes, 1000215216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x79843b02


Device     Boot     Start        End   Sectors   Size Id Type
/dev/sda1  *         2048     718847    716800   350M  7 HPFS/NTFS/exFAT
/dev/sda2          718848  999290879 998572032 476.2G  7 HPFS/NTFS/exFAT
/dev/sda3       999290880 1000212479    921600   450M 27 Hidden NTFS WinRE




Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: E6AFF16F-8523-4ACC-9F14-F927AC9BD6F1


Device      Start        End    Sectors  Size Type
/dev/sdb1      34     262177     262144  128M Microsoft reserved
/dev/sdb2  264192 3907028991 3906764800  1.8T Microsoft basic data


Partition 1 does not start on physical sector boundary.




Disk /dev/sdc: 698.7 GiB, 750156374016 bytes, 1465149168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x5ab2bc41


Device     Boot      Start        End   Sectors   Size Id Type
/dev/sdc1  *          2048     206847    204800   100M  7 HPFS/NTFS/exFAT
/dev/sdc2           206848  566437887 566231040   270G  7 HPFS/NTFS/exFAT
/dev/sdc3        566437888 1414586367 848148480 404.4G  f W95 Ext'd (LBA)
/dev/sdc4       1414586368 1465147391  50561024  24.1G 27 Hidden NTFS WinRE
/dev/sdc5        566439936 1414586367 848146432 404.4G  7 HPFS/NTFS/exFAT


Partition table entries are not in disk order.




Disk /dev/sdd: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x9925f06e


Device     Boot Start       End   Sectors   Size Id Type
/dev/sdd1        2048 976769023 976766976 465.8G  7 HPFS/NTFS/exFAT




Disk /dev/sde: 57.7 GiB, 61951967232 bytes, 120999936 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x04996f28


Device     Boot Start       End   Sectors  Size Id Type
/dev/sde1  *     2048 120999935 120997888 57.7G  c W95 FAT32 (LBA)




Disk /dev/sdf: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disklabel type: gpt
Disk identifier: C3C340AE-0FB5-4F53-BE47-BCDBE3A1F926


Device          Start        End    Sectors  Size Type
/dev/sdf1        2048    1050623    1048576  512M Linux swap
/dev/sdf2     3147776 5858433899 5855286124  2.7T Microsoft basic data
/dev/sdf3  5858435072 5860533134    2098063    1G Microsoft basic data
/dev/sdf4     1050624    3147775    2097152    1G Microsoft basic data


Partition table entries are not in disk order.

```

I used sudo mkdir to create a 3T directory then tried to mount to it with the below command but get an error



```

knoppix@Microknoppix:~$ sudo mount -t ext2 /dev/sdf2/ /3T
mount: special device /dev/sdf2/ does not exist (a path prefix is not a directory)

```


What do I need to do?

---

### Post by TheFu on 2018-06-04
Can't tell from  the provided data. Sorry.

Need to know the file system type.  In theory, you shouldn't need to specify the file system.
**sudo mount  /dev/sdf2 /mnt**
is what I'd try.  I'm making lots of assumptions.  Understanding device locations and directories is important.

Knoppix isn't Ubuntu and the NAS isn't running Ubuntu either.

---

