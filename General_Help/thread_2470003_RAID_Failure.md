---
title: "RAID Failure"
date: 2021-12-16
forum: General Help
---

### Post by TPrime on 2021-12-16
My server's RAID5 failed today, and mdadm is giving me some weird information.

First 'mdadm' lists the array as raid0, when it should be raid5.

```
/dev/md127:
           Version : 1.2
        Raid Level : raid0
     Total Devices : 4
       Persistence : Superblock is persistent

             State : inactive
   Working Devices : 4

              Name : ubuntu-server:Data_RAID
              UUID : e53ba358:1a0b2928:60fa66ce:d96f4138
            Events : 5967434

    Number   Major   Minor   RaidDevice

       -       8       64        -        /dev/sde
       -       8        0        -        /dev/sda
       -       8       48        -        /dev/sdd
       -       8       16        -        /dev/sdb

```

Then when checking each disk they don't agree on which devices are missing.
```
/dev/sda:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : e53ba358:1a0b2928:60fa66ce:d96f4138
           Name : ubuntu-server:Data_RAID
  Creation Time : Tue Jul 23 01:24:47 2019
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3906764976 (1862.89 GiB 2000.26 GB)
     Array Size : 5860147200 (5588.67 GiB 6000.79 GB)
  Used Dev Size : 3906764800 (1862.89 GiB 2000.26 GB)
    Data Offset : 264192 sectors
   Super Offset : 8 sectors
   Unused Space : before=264112 sectors, after=176 sectors
          State : clean
    Device UUID : 6f797783:0f21ab6a:69266265:14c4635b

Internal Bitmap : 8 sectors from superblock
    Update Time : Sun Dec  5 00:57:01 2021
  Bad Block Log : 512 entries available at offset 16 sectors
       Checksum : 6b8d409a - correct
         Events : 5967440

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : .A.A ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdb:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x9
     Array UUID : e53ba358:1a0b2928:60fa66ce:d96f4138
           Name : ubuntu-server:Data_RAID
  Creation Time : Tue Jul 23 01:24:47 2019
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3906764976 (1862.89 GiB 2000.26 GB)
     Array Size : 5860147200 (5588.67 GiB 6000.79 GB)
  Used Dev Size : 3906764800 (1862.89 GiB 2000.26 GB)
    Data Offset : 264192 sectors
   Super Offset : 8 sectors
   Unused Space : before=264112 sectors, after=176 sectors
          State : clean
    Device UUID : b2dd7d4b:a524b4b6:f80cb48e:b4c96bc6

Internal Bitmap : 8 sectors from superblock
    Update Time : Sun Dec  5 00:57:01 2021
  Bad Block Log : 512 entries available at offset 16 sectors - bad blocks present.
       Checksum : 13f69538 - correct
         Events : 5967440

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : .A.A ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdd:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : e53ba358:1a0b2928:60fa66ce:d96f4138
           Name : ubuntu-server:Data_RAID
  Creation Time : Tue Jul 23 01:24:47 2019
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3906764976 (1862.89 GiB 2000.26 GB)
     Array Size : 5860147200 (5588.67 GiB 6000.79 GB)
  Used Dev Size : 3906764800 (1862.89 GiB 2000.26 GB)
    Data Offset : 264192 sectors
   Super Offset : 8 sectors
   Unused Space : before=264112 sectors, after=176 sectors
          State : clean
    Device UUID : 23448303:be388788:1628ea60:0186e328

Internal Bitmap : 8 sectors from superblock
    Update Time : Tue Jul 27 00:34:58 2021
  Bad Block Log : 512 entries available at offset 16 sectors
       Checksum : d173ef57 - correct
         Events : 53434

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sde:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : e53ba358:1a0b2928:60fa66ce:d96f4138
           Name : ubuntu-server:Data_RAID
  Creation Time : Tue Jul 23 01:24:47 2019
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3906764976 (1862.89 GiB 2000.26 GB)
     Array Size : 5860147200 (5588.67 GiB 6000.79 GB)
  Used Dev Size : 3906764800 (1862.89 GiB 2000.26 GB)
    Data Offset : 264192 sectors
   Super Offset : 8 sectors
   Unused Space : before=264112 sectors, after=176 sectors
          State : clean
    Device UUID : 1860eee9:458f6d4d:afa39c8e:07fb048a

Internal Bitmap : 8 sectors from superblock
    Update Time : Thu Nov 25 14:03:43 2021
  Bad Block Log : 512 entries available at offset 16 sectors
       Checksum : c94d6a9 - correct
         Events : 5967434

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : .AAA ('A' == active, '.' == missing, 'R' == replacing)

```

Can anyone provide insight on how I might be able to resolve this?

Thank you.

---

### Post by TheFu on 2021-12-17
Check for loose cables. Had a cable that would vibrate loose every few months. After screwing with it for over a year, I replaced all the cables with 90 deg cables and haven't had that issue again.  A few disks have failed, but they were mostly non-events.  I keep notes for the steps to replace a failed disk.
The commands below are *ticklers*, not to be copy/pasted, but to serve as reminders for the commands and parameters. Change as needed.

# ##############################################
# Don't forget to check and repair the RAID periodically. 
# RAID Maintenance
echo check > /sys/block/mdX/md/sync_action
echo repair > /sys/block/mdX/md/sync_action

# ##############################################
# Review the Array config - Missing/Failed
sudo mdadm --detail /dev/md0
# Verify that the failed drive is seen by the OS
ls -l /dev/sd*1

# Clone the partition table from the working RAID disk
# ############[ IMPORTANT ]##############
# ########[ [COLOR="#FF0000"]This is backwards from normal[/COLOR] ]##############
     sdd (source) --> sdc (target)
sgdisk -R /dev/sdc /dev/sdd
# ########[ [COLOR="#FF0000"]This is backwards from normal[/COLOR] ]##############

# Force a new GUID - don't want the same one as the source
sgdisk -G /dev/sdc

# Fail, then Remove the failed disk/partition 
more /proc/mdstat 
sudo mdadm --manage /dev/md1  [COLOR="#FF0000"]--fail[/COLOR] /dev/sde2
more /proc/mdstat 
sudo mdadm --manage /dev/md1  [COLOR="#FF0000"]--remove[/COLOR]  /dev/sde2
more /proc/mdstat 
# Shutdown the box, physically replace the disk.

# Tell mdadm to use this new partition in the array
mdadm --manage /dev/md1 --add /dev/sdc3

# Watch the sync progress in /proc/mdstat - 2TB takes about 4 hrs.

I find it best to physically label the devices with the WWN in a location I can see easily without removing the disk. Then some disk tools will tell us exactly which device failed by the WWN.  The mapping is in /dev/disk/by-id/ if the tool you use doesn't clearly way WWN xyz1234 failed. Follow the symlinks to the device. For example:
```

lrwxrwxrwx 1 root root  9 Dec 17 01:45 wwn-0x5000039ff3e204bb -> ../../sdd
lrwxrwxrwx 1 root root 10 Dec 17 01:45 wwn-0x5000039ff3e204bb-part1 -> ../../sdd1
lrwxrwxrwx 1 root root 10 Dec 17 01:45 wwn-0x5000039ff3e204bb-part2 -> ../../sdd2
lrwxrwxrwx 1 root root 10 Dec 17 01:45 wwn-0x5000039ff3e204bb-part3 -> ../../sdd3
lrwxrwxrwx 1 root root 10 Dec 17 01:45 wwn-0x5000039ff3e204bb-part4 -> ../../sdd4
lrwxrwxrwx 1 root root  9 Dec 17 01:45 wwn-0x5000cca223c1ac77 -> ../../sde
lrwxrwxrwx 1 root root 10 Dec 17 01:45 wwn-0x5000cca223c1ac77-part1 -> ../../sde1
lrwxrwxrwx 1 root root 10 Dec 17 01:45 wwn-0x5000cca223c1ac77-part2 -> ../../sde2
lrwxrwxrwx 1 root root  9 Dec 17 01:45 wwn-0x50014ee05644b57e -> ../../sdc
lrwxrwxrwx 1 root root 10 Dec 17 01:45 wwn-0x50014ee05644b57e-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 Dec 17 01:45 wwn-0x50014ee05644b57e-part2 -> ../../sdc2
lrwxrwxrwx 1 root root 10 Dec 17 01:45 wwn-0x50014ee05644b57e-part3 -> ../../sdc3
lrwxrwxrwx 1 root root 10 Dec 17 01:45 wwn-0x50014ee05644b57e-part4 -> ../../sdc4
lrwxrwxrwx 1 root root 10 Dec 17 01:45 wwn-0x50014ee05644b57e-part5 -> ../../sdc5
lrwxrwxrwx 1 root root  9 Dec 17 01:45 wwn-0x50014ee058deaf74 -> ../../sdg
lrwxrwxrwx 1 root root 10 Dec 17 01:45 wwn-0x50014ee058deaf74-part1 -> ../../sdg1
lrwxrwxrwx 1 root root 10 Dec 17 01:45 wwn-0x50014ee058deaf74-part2 -> ../../sdg2
lrwxrwxrwx 1 root root 10 Dec 17 01:45 wwn-0x50014ee058deaf74-part3 -> ../../sdg3
lrwxrwxrwx 1 root root  9 Dec 17 01:45 wwn-0x50014ee058dee0a9 -> ../../sdf
lrwxrwxrwx 1 root root 10 Dec 17 01:45 wwn-0x50014ee058dee0a9-part1 -> ../../sdf1
lrwxrwxrwx 1 root root 10 Dec 17 01:45 wwn-0x50014ee058dee0a9-part2 -> ../../sdf2
lrwxrwxrwx 1 root root 10 Dec 17 01:45 wwn-0x50014ee058dee0a9-part3 -> ../../sdf3
lrwxrwxrwx 1 root root  9 Dec 17 01:45 wwn-0x50024e9004bc36d3 -> ../../sdb
lrwxrwxrwx 1 root root 10 Dec 17 01:45 wwn-0x50024e9004bc36d3-part1 -> ../../sdb1
```
and those can be mapped to the RAID using:
```
$ more /proc/mdstat 
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid1 sdg2[1] sdf2[0]
      1338985536 blocks [2/2] [UU]
      
md1 : active raid1 sde2[3] sdd3[2]
      1943010816 blocks super 1.2 [2/2] [UU]
```
I include this data in nightly, versioned, backup data, so when a device fails, I have 120 days of backups with the data, if there were any changes over time.  Backups are a great place to keep system information to recover from HW failures.

I switched from RAID5 to RAID1 with the move to 2TB disks long ago. I don't recall the exact lesson, but I remember RAID5 taught me a hard lesson.

There's usually an LED that doesn't shine when a drive fails.  Then you can just pull the old drive, replace it with a new one as spelled out above. 
If the server has some less busy times, tweak the I/O slice that rebuilding the array gets to be higher when usage is low.

Somehow, disk issues seem to know how good our backups are.  With great backups, I don't seem to have nearly as many disk problems as when I didn't have backup religion.

---

