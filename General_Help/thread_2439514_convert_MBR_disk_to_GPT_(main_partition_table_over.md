---
title: "convert MBR disk to GPT (main partition table overlaps by 33 blocks)"
date: 2020-03-28
forum: General Help
---

### Post by skrewler on 2020-03-28
I've got a Percona MySQL DB running in EC2 that I've had to continually add space to the EBS volume, then grow it (using growpart/xfs_growfs).  I finally hit 2TB and couldn't figure out why it wasn't working, its because of course it's an MBR partition table.  Running Ubuntu


The thing is, these DBs are in a cluster w/ (what I thought was) the exact same configurations.  On the others, I was able to convert to GPT without any errors.  It's just this one that I'm having trouble with.


Thanks in advance


Here are the outputs of gdisk, parted, fdisk.


I'm a bit confused why the xvdn1 shows as GPT but not xvdn .. I might have screwed up somewhere in the past?


What is the best way forward?


```
```
gdisk /dev/xvdn
GPT fdisk (gdisk) version 0.8.8


Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present




***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by
typing 'q' if you don't want to convert your MBR partitions
to GPT format!
***************************************************************


Warning! Main partition table overlaps the first partition by 33 blocks!
You will need to delete this partition or resize it in another utility.

``````


```
```
parted /dev/xvdn unit s print
Model: Xen Virtual Block Device (xvd)
Disk /dev/xvdn: 5033164800s
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start  End          Size         Type     File system  Flags
 1      1s     4194298394s  4194298394s  primary  xfs

``````


```
```
parted /dev/xvdn1 unit s print
Model: Unknown (unknown)
Disk /dev/xvdn1: 4194298394s
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start  End  Size  File system  Name  Flags

``````


```
```
fdisk -l -u /dev/xvdn


Disk /dev/xvdn: 2577.0 GB, 2576980377600 bytes
255 heads, 63 sectors/track, 313300 cylinders, total 5033164800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b6274


    Device Boot      Start         End      Blocks   Id  System
/dev/xvdn1               1  4194298394  2097149197   83  Linux

``````


```
```
lsblk /dev/xvdn
NAME    MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
xvdn    202:208  0   2.4T  0 disk
&#9492;&#9472;xvdn1 202:209  0     2T  0 part

``````


Made backups ...
```
```
dd if=/dev/xvdn of=/root/mbrbackups/xvdnbackup.mbr bs=512 count=1


sfdisk -d /dev/xvdn > sfdiskbackup.txt
cat sfdiskbackup.txt
# partition table of /dev/xvdn
unit: sectors


/dev/xvdn1 : start=        1, size=4194298394, Id=83
/dev/xvdn2 : start=        0, size=        0, Id= 0
/dev/xvdn3 : start=        0, size=        0, Id= 0
/dev/xvdn4 : start=        0, size=        0, Id= 0

``````








Note: I see similar questions/answers but they seem a bit different than mine.  In my case, I only have 1 partition on a disk.  I've also gone thru this procedure on (what I thought) was the same configuration, and was able to do the procedure w/o any error.. this one system Im having issues

---

### Post by oldfred on 2020-03-28
See also:
[https://askubuntu.com/questions/1222097/convert-mbr-disk-to-gpt-main-partition-table-overlaps-by-33-blocks](https://askubuntu.com/questions/1222097/convert-mbr-disk-to-gpt-main-partition-table-overlaps-by-33-blocks)

What version of sfdisk are you using? Old  versions did not support gpt, new versions do, but partition table backup  includes more data for gpt than you show. 
You should have good backup of partition table, but also good backup of all your data.

last partition overlaps backup partition table
 [ubuntuforums.org/showthread.php?t=1956173]("http://ubuntuforums.org/showthread.php?t=1956173") 
Check start & end, delete and recreate without overlap. 
Backup vital just in case.

[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

---

### Post by skrewler on 2020-03-29
I replied on stackoverflow, just going to delete the question there


[COLOR=#000000] partition table backup includes more data for gpt than you show.[/COLOR]

That's all thats shown, I assume cause it's still a GPT disk.  I realize I made a long post, so it's perhaps a bit confusing.  but i'm trying to convert from MBR to GPT, but get that error.  For some reason tho, /dev/xvdn1 shows as a GPT disk.  Is that even possible?  for the /dev/xvdn partition table to be mbr, but the /dev/xvdn1 partition to be GPT?  doesn't make sense.  maybe thats the source of my problems.

I don't know what you mean by this:


[COLOR=#000000]Check start & end, delete and recreate without overlap.


[/COLOR]

---

### Post by skrewler on 2020-03-29
```

gdisk /dev/xvdn
GPT fdisk (gdisk) version 0.8.8


Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present




***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by
typing 'q' if you don't want to convert your MBR partitions
to GPT format!
***************************************************************


Warning! Main partition table overlaps the first partition by 33 blocks!
You will need to delete this partition or resize it in another utility.

Command (? for help): i
Using 1
Partition GUID code: 0FC63DAF-8483-4772-8E79-3D69D8477DE4 (Linux filesystem)
Partition unique GUID: FBBD14FF-CE1E-4843-93E7-03C5B8C239C7
First sector: 1 (at 512 bytes)
Last sector: 4194298394 (at 2.0 TiB)
Partition size: 4194298394 sectors (2.0 TiB)
Attribute flags: 0000000000000000
Partition name: 'Linux filesystem'


Command (? for help): p
Disk /dev/xvdn: 4613734400 sectors, 2.1 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 5B872CDE-9E87-4600-98B2-3C4639E683B1
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 4613734366
Partitions will be aligned on 8-sector boundaries
Total free space is 419435972 sectors (200.0 GiB)


Number  Start (sector)    End (sector)  Size       Code  Name
   1               1      4194298394   2.0 TiB     8300  Linux filesystem


Command (? for help): v
Warning! Main partition table overlaps the first partition by 33 blocks!
You will need to delete this partition or resize it in another utility.


Caution: Partition 1 doesn't begin on a 8-sector boundary. This may
result in degraded performance on some modern (2009 and later) hard disks.


Consult http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/
for information on disk alignment.


Identified 1 problems!

```

---

### Post by oldfred on 2020-03-29
I do not know virtual disks, but I believe you can create it as if it is just hardware. So I would expect that it could be gpt.

The gdisk output has a warning and says the same thing. You need to shrink partition.
But in your case the partition starts at sector 1 which is not allowed. You have to have a minimum number of sectors at beginning of drive for the gpt partition table info. 

You need to change start from 1 to 34, but if new 4K drive it should be 40.
GPT (partitioning schema) on the hard disk drive is located in first 34 and last 33 sectors
[http://askubuntu.com/questions/460233/cant-restore-my-gpt-data-with-gdisk](http://askubuntu.com/questions/460233/cant-restore-my-gpt-data-with-gdisk)

First usable sector is 34.

Rod Smith is author of gdisk.
GPT (partitioning schema) on the hard disk drive is located in first 34 and last 33 sectors .
[http://askubuntu.com/questions/460233/cant-restore-my-gpt-data-with-gdisk](http://askubuntu.com/questions/460233/cant-restore-my-gpt-data-with-gdisk)

Partition does not start on physical sector boundary.
First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). 
[https://developer.ibm.com/technologies/linux/](https://developer.ibm.com/technologies/linux/)
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

---

### Post by TheFu on 2020-03-29
Stuff like this is when using LVM really shines, though i wouldn't use XFS unless i was absolutely positive to never need to reduce any LVs.

---

### Post by skrewler on 2020-03-29
> **TheFu said:**
> Stuff like this is when using LVM really shines, though i wouldn't use XFS unless i was absolutely positive to never need to reduce any LVs.

i use LVM on all my onprem systems.

don't really feel the need in the cloud/AWS.

this problem is just a weird ass issue i'm running into on this one drive .. i have 14 other DBs that I was able to convert to GPT w/ no issue.  this is the only one.

---

### Post by skrewler on 2020-03-29
> **oldfred said:**
> I do not know virtual disks, but I believe you can create it as if it is just hardware. So I would expect that it could be gpt.

The gdisk output has a warning and says the same thing. You need to shrink partition.
But in your case the partition starts at sector 1 which is not allowed. You have to have a minimum number of sectors at beginning of drive for the gpt partition table info. 

You need to change start from 1 to 34, but if new 4K drive it should be 40.
GPT (partitioning schema) on the hard disk drive is located in first 34 and last 33 sectors
[http://askubuntu.com/questions/460233/cant-restore-my-gpt-data-with-gdisk](http://askubuntu.com/questions/460233/cant-restore-my-gpt-data-with-gdisk)

First usable sector is 34.

Rod Smith is author of gdisk.
GPT (partitioning schema) on the hard disk drive is located in first 34 and last 33 sectors .
[http://askubuntu.com/questions/460233/cant-restore-my-gpt-data-with-gdisk](http://askubuntu.com/questions/460233/cant-restore-my-gpt-data-with-gdisk)

Partition does not start on physical sector boundary.
First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). 
[https://developer.ibm.com/technologies/linux/](https://developer.ibm.com/technologies/linux/)
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

Ok, I get the problem now -- I see the disks that worked weren't starting at 1.  However, everytime I delete/recreate partition table, I get this when I try to mount it: 

```mount: /mnt/test: wrong fs type, bad option, bad superblock on /dev/xvdh1, missing codepage or helper program, or other error.```

is it possible to fix this while keeping my data?

---

### Post by oldfred on 2020-03-29
If you have data in those first 40 sectors, you cannot move partition to start at sector 40 without damaging it.
Not sure how to do it other than backup data, create new partition table with correct gpt structure and restore data.

What tool were you using to create partition table?
I have used gparted & gdisk, whatever is current versions at the time. But older tools may not work as well.

---

