---
title: "Primary GPT errors on RAID5 members"
date: 2017-03-16
forum: General Help
---

### Post by warpnacelle on 2017-03-16
Hello world,

Firstly, apologies if this has been answered previously. I have searched but could not seem to find the answers specific to my question.

I have 5x 4TB drives in a RAID5 array using mdadm. Whilst I was using fdisk to check something on an old SSD, fdisk -l showed that two of the drives in the array had primary GPT errors and were using the backup

I've found numerous articles saying that it can be fixed by running gdisk on the drives, however my question is, will that cause problems on the data in the array?

Bit of a noob - I know enough linux to do basic tasks. I thought that a GPT was a partition table and assumed that the raid device created md127 would technically have the GPT?

Would appreciate some assistance. The array is quite full so want to avoid rebuilding/losing the data

here's some outputs:

```
 sudo fdisk -l

-- 15 ram disks omitted --

Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x702efe41

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *         2048 471871487 471869440  225G 83 Linux
/dev/sda2       471873534 488396799  16523266  7.9G  5 Extended
/dev/sda5       471873536 488396799  16523264  7.9G 82 Linux swap / Solaris


Disk /dev/sdb: 119.2 GiB, 128035676160 bytes, 250069680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000d0dfd

Device     Boot Start       End   Sectors   Size Id Type
/dev/sdb1        2048 250069679 250067632 119.2G 83 Linux


Disk /dev/sdc: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sdd: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


The primary GPT table is corrupt, but the backup appears OK, so that will be used.
Disk /dev/sde: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 94BD9765-3F4E-4EC2-A391-77E13BC2329C


The primary GPT table is corrupt, but the backup appears OK, so that will be used.
Disk /dev/sdf: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 185120B3-2887-4847-8515-A024E0AA76D6


Disk /dev/sdg: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sdh: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/md0: 14.6 TiB, 16002609840128 bytes, 31255097344 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 524288 bytes / 2097152 bytes

```

gdisk on one of the above drives with an error
```
 sudo gdisk /dev/sde
GPT fdisk (gdisk) version 1.0.1

Caution! After loading partitions, the CRC doesn't check out!
Warning! Main partition table CRC mismatch! Loaded backup partition table
instead of main partition table!

Warning! One or more CRCs don't match. You should repair the disk!

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************

Command (? for help):
```

gdisk on device without errors:
```
 sudo gdisk /dev/sdd
GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.

Command (? for help):
```

drive info from mdadm:
```
sudo mdadm -E /dev/sde
/dev/sde:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : df447c4d:ea492dd0:1a3822c3:9ea57c1b
           Name : bigblackdisks:0
  Creation Time : Sun Aug 31 14:30:13 2014
     Raid Level : raid5
   Raid Devices : 5

 Avail Dev Size : 7813775024 (3725.90 GiB 4000.65 GB)
     Array Size : 15627548672 (14903.59 GiB 16002.61 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262064 sectors, after=688 sectors
          State : clean
    Device UUID : 51843e3d:e9f4009d:f12f5342:eadce0f2

Internal Bitmap : 8 sectors from superblock
    Update Time : Thu Mar 16 16:12:19 2017
       Checksum : 51f00fe3 - correct
         Events : 59989

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : AAAAA ('A' == active, '.' == missing, 'R' == replacing)
```

---

### Post by warpnacelle on 2017-03-20
bump. anyone?

---

