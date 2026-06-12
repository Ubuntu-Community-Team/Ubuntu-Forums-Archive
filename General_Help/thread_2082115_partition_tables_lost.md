---
title: "partition tables lost"
date: 2012-11-08
forum: General Help
---

### Post by michaelza on 2012-11-08
I have a dedicated server with 2 500GB harddisks and suddenly the partition tabels on both disks see to be lost.
This is at least what the guy from tech support there told me. Strange situation, as I have not done anything for sure.
Not even made a backup on the tables before ;o(((

I have now started reading through postings and have collected here all I found out and all I know about the old state - which is not all too much.

I have the box online now booted from some recovery system.
Is there any chance to get the filesystem back?

There are 6 GB RAM and 2 500GB disks in the box, originally I installed Ubuntu 8.04 with the default disk partioning settings proposed by the installation on /dev/sda. The other drive was kept unused for some time.



```

root@mybox123:~# fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

```

```

root@mybox123:~# parted /dev/sdb
GNU Parted 2.3
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) rescue 0 976773168
Error: /dev/sdb: unrecognised disk label

```

```

TestDisk 6.13, Data Recovery Utility, November 2011
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
OS: Linux, kernel 3.2.14-live-ig2 (#1 SMP Tue May 8 12:49:15 CEST 2012) x86_64
Compiler: GCC 4.6
Compilation date: 2012-02-05T07:15:52
ext2fs lib: 1.42, ntfs lib: 10:0:0, reiserfs lib: none, ewf lib: none
/dev/sda: LBA, HPA, LBA48, DCO support
/dev/sda: size       976773168 sectors
/dev/sda: user_max   976773168 sectors
/dev/sda: native_max 976773168 sectors
/dev/sda: dco        976773168 sectors
/dev/sdb: LBA, HPA, LBA48, DCO support
/dev/sdb: size       976773168 sectors
/dev/sdb: user_max   976773168 sectors
/dev/sdb: native_max 976773168 sectors
/dev/sdb: dco        976773168 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
Warning: can't get size for Disk /dev/md0 - 0 B - CHS 1 2 4, sector size=512
Hard disk list
Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63, sector size=512 - WDC WD5000AADS-00S9B0, S/N:WD-WCAV93359795, FW:01.00A01
Disk /dev/sdb - 500 GB / 465 GiB - CHS 60801 255 63, sector size=512 - WDC WD5000AADS-00S9B0, S/N:WD-WCAV93359558, FW:01.00A01

Partition table type (auto): Intel
Disk /dev/sda - 500 GB / 465 GiB - WDC WD5000AADS-00S9B0
Partition table type: Intel

Analyse Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
Current partition structure:

Partition sector doesn't have the endmark 0xAA55
Ask the user for vista mode
Computes LBA from CHS for Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63
Allow partial last cylinder : Yes
search_vista_part: 1

search_part()
Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63

Results

interface_write()
 
No partition found or selected for recovery
SIGHUP detected! TestDisk has been killed.

```

---

### Post by michaelza on 2012-11-08
Also did some SMART testing and readout with smartctl. Output does not show any disk errors.


For the 2nd disk /dev/sdb I lateron put just one max sized partion on it, formated it with ext3 and mounted it:

```

mybox123:~# mkfs -t ext3 /dev/sdb1
mke2fs 1.41.11 (14-Mar-2010)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
30531584 inodes, 122096390 blocks
6104819 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
3727 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
        102400000

Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information:  done

This filesystem will be automatically checked every 30 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

mybox123:~#  tune2fs -m 0 /dev/sdb1
tune2fs 1.41.11 (14-Mar-2010)
Setting reserved blocks percentage to 0% (0 blocks)

mybox123:/media# mount /dev/sdb1 /media/hd2

```

Is there a way to guess how the pation tabels should be? 
As I know the exact size of disks, the RAM (thus the swap size Ubuntu 8.04 will propose). And that the 2nd disk was I full ext3 partition.

Any chance?

---

### Post by hal8000 on 2012-11-08
How many partitions did you setup originally?
Did you have /,  /home and /swap ?

I always create a backup of my partition table on paper, using libre Office
as I have multiboot and know exact start and end sectors of each partition.

Guessing this information will lead to data loss.

Now that youve created a new partition table, the old data may have been overwritten. Testdisk can search for lost partition tables, you need to boot from the Ubuntu CD in live mode then start testdisk from terminal.
8.04 is quite old, so not sure if its included on live CD.

Anyway a link below for reference:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status)

---

### Post by michaelza on 2012-11-08
Hello hal,
thank you for the reply.

I had later upgraded to Ubuntu 10.04, without making any changes to the partitions.
partions were: / , /swap and /boot
I am currently analysing the disks with testdisk ...

You were writing: 
> Now that youve created a new partition table ...

I did not create anything. Does it look like a new partition table has been written?
Maybe the techguy from my provider screwed up the disk?

It is VERY strange to me that in a well running server without any disk errors (none logged by smart after over 20k hours of running) that on such a box from one hour to the next both partitiontables of 2 independent disks are all blank.

Ever heard of something like this?

Kind regards
Michael

---

### Post by michaelza on 2012-11-08
Any ideas what could make partition tables vanish?

* I am the only one with access to the box
* no errors on disk smart logs
* drives independently with ext3 filesystems on them, sdb just mounted
* no RAID

strange story

My suspect is the tech guy whom I ask to check why the server was offline - I am not sure if he did not destroy the tables while looking for an error on disk ...

---

