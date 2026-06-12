---
title: "mdadm"
date: 2014-01-13
forum: General Help
---

### Post by Slownis on 2014-01-13
I have a newly created raid 5 array, migrated from a raid 1 when I got a third drive for christmas.  This is on a ubuntu 12.04 LTS machine.

The original raid 1 array consisted of 2 2TB green drives that I set up.  Each drive had an identical single ext4 partition encompassing the entire drive and the raid was built over the partition.  These are non system - meaning the ubuntu install is on a completely separate drive.

So when got a 3rd WD 2TB green drive I happily went googling and followed some guides to migrate my raid 1 to a raid 5 setup with 3 drives.
Basic steps I took:
1) Fail and remove 1 drive from the raid 1 (md0), zeroing the superblock, dd'ing the partition.
2) Create new raid 5 array (md5) consisting of the new drive (sdb), the drive I removed from the raid 1 (sdc), and a missing drive.  This raid was built over the devices, not partitions. (sdb vs sdb1, etc.)
3) Used dd to copy md0 device to md5.
4) Failed and removed the remaining drive (sdd) from md0,  zeroed the superblock, and destroyed md0.
5) Added sdd to the new md5 array, reset mdadm.conf, fstab, [COLOR=#000000]update initramfs.

And so in a perfect world, I should have ended up with a 4TB raid 5 array built over individual devices (sd[b-d] with data identical to the original raid 1 array that was built over individual partitions [sdc1 and sdd1] on the devices.

The new array seems to be working fine, except something strange has happened, making me question if I skipped a step somewhere along the way. 

[/COLOR]```
johnw@johnw-desktop:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md5 : active raid5 sdc[1] sdd[3] sdb[0]
      3906765824 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]

```[COLOR=#000000]

mdadm examine each of the devices in the array:
[/COLOR]```
johnw@johnw-desktop:~$ sudo mdadm --examine /dev/sd[b-d]
[sudo] password for johnw: 
/dev/sdb:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 52c035ba:7524c0e7:9ae73d40:d13ef8b4
           Name : johnw-desktop:5  (local to host johnw-desktop)
  Creation Time : Wed Jan  8 17:58:05 2014
     Raid Level : raid5
   Raid Devices : 3


 Avail Dev Size : 3906767024 (1862.89 GiB 2000.26 GB)
     Array Size : 3906765824 (3725.78 GiB 4000.53 GB)
  Used Dev Size : 3906765824 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 7633c60b:e8acf681:6ca1ef1a:36cc153d


    Update Time : Mon Jan 13 11:16:26 2014
       Checksum : e0b5540a - correct
         Events : 21143


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 0
   Array State : AAA ('A' == active, '.' == missing)
/dev/sdc:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 52c035ba:7524c0e7:9ae73d40:d13ef8b4
           Name : johnw-desktop:5  (local to host johnw-desktop)
  Creation Time : Wed Jan  8 17:58:05 2014
     Raid Level : raid5
   Raid Devices : 3


 Avail Dev Size : 3906767024 (1862.89 GiB 2000.26 GB)
     Array Size : 3906765824 (3725.78 GiB 4000.53 GB)
  Used Dev Size : 3906765824 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : b35a61bd:e3027883:0be588d7:6b98abd3


    Update Time : Mon Jan 13 11:16:26 2014
       Checksum : e700e119 - correct
         Events : 21143


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 1
   Array State : AAA ('A' == active, '.' == missing)
/dev/sdd:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 52c035ba:7524c0e7:9ae73d40:d13ef8b4
           Name : johnw-desktop:5  (local to host johnw-desktop)
  Creation Time : Wed Jan  8 17:58:05 2014
     Raid Level : raid5
   Raid Devices : 3


 Avail Dev Size : 3906767024 (1862.89 GiB 2000.26 GB)
     Array Size : 3906765824 (3725.78 GiB 4000.53 GB)
  Used Dev Size : 3906765824 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 1816504c:f6de06bc:3f9103cc:2dbd98a7


    Update Time : Mon Jan 13 11:16:26 2014
       Checksum : 76e64989 - correct
         Events : 21143


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 2
   Array State : AAA ('A' == active, '.' == missing)

```

Heres the weird thing:
```
johnw@johnw-desktop:~$ sudo fdisk -l


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0007ae28


   Device Boot      Start         End      Blocks   Id  System
**/dev/sdb1            2048  3907028991  1953513472   fd  Linux raid autodetect**


WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


**Disk /dev/sdc doesn't contain a valid partition table**


WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


**Disk /dev/sdd doesn't contain a valid partition table**


Disk /dev/md5: 4000.5 GB, 4000528203776 bytes
2 heads, 4 sectors/track, 976691456 cylinders, total 7813531648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disk identifier: 0x00000000


Disk /dev/md5 doesn't contain a valid partition table



```

sdb (my new drive) has a partition on it while sdc and sdd do not.  This is causing some weird behaviors, although md5 appears to be working.  Namely, the sdb1 partition is visible to the OS, but it is unmountable.  Is there a way I can move the sdb1 partition without degrading my new md5 array?

---

### Post by TheFu on 2014-01-13
Current fdisk shouldn't be used.  Please check with **parted -l**.  Besides that, I've never migrated in the way you did. Always prefer using a backup, but that is just me.

Also, green drives often don't have some important features needed for RAID use. I hope the software takes that into account. Part of the work-around, I believe, is disabling the automatic spin-down, but don't quote me. 

Thinking about the error again, it appears the new HDD came with GPT format - hopefully the parted command will provide more details. It really should be the go-to command ever since GPT disks started showing up. There is enough backwards compatibility in the GPT format to prevent complete barfing by fdisk, but ...   If removal of the GPT is needed, that does require wiping the HDD (as far as mdadm is concerned).

RAID is never a replacement for good backups.

---

### Post by Slownis on 2014-01-13
Here is the output from parted -l

The WD20EZRX drive (sdb) is the only drive in the array that lists a partition.  The drives being 2TB I could swear I originally formatted each drive as MBR, so I'm not sure where the GPT came from in the fdisk command. I've been using the 2 green drives for over 6 months in an mdadm raid 1 config, and I never did anything with the automatic spin down "feature"

```
johnw@johnw-desktop:~$ sudo parted -l
[sudo] password for johnw: 
Model: ATA WDC WD20EZRX-00D (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ext4         raid [COLOR=#ff0000]<< this sdb partition should not be there.  Is there a way to remove it without tearing down the array?[/COLOR]




Error: /dev/sdc: unrecognised disk label                                  


Error: /dev/sdd: unrecognised disk label                                  


Model: Linux Software RAID Array (md)
Disk /dev/md5: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop


Number  Start  End     Size    File system  Flags
 1      0.00B  4001GB  4001GB  ext4
```

---

### Post by Slownis on 2014-01-14
OK, I took a chance and removed the sdb1 partition in gparted.  everything is looking good.  Except for one thing, I'm not using all of my array size:
```
johnw@johnw-desktop:~$ sudo mdadm --detail /dev/md5
/dev/md5:
        Version : 1.2
  Creation Time : Wed Jan  8 17:58:05 2014
     Raid Level : raid5
     Array Size : [COLOR=#ff0000]3906766848[/COLOR] (3725.78 GiB 4000.53 GB)
  Used Dev Size : [COLOR=#ff0000]1953383424[/COLOR] (1862.89 GiB 2000.26 GB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent
```

How can I make md5 use the full array size?

---

### Post by rubylaser on 2014-01-14
First thing.  Your initial partition error was fine.  You had an unnecessary partition on /dev/sdb, but mdadm was using the whole RAW disk, so all is well.  Also, your array is already using all available space.  Disk manufacturers quote a Kilobyte as 1,000 Bytes, but in reality there are 1,024 Bytes in a Kilobytes. So, for a 2TB disk, that would leave you with ~1863GB per disk. A GB is 2^30 bytes or 1,073,741,824. Here's the math. 
```

2,000,000,000 bytes / 1,073,741,824  = 1.8626451492 x 1000 = ~1862.65 GB

```
And that number doubled is.... You guessed it :) 3,725.78 GB of usable space or exactly what mdadm shows as usable space. I hope that helps.

---

### Post by Slownis on 2014-01-14
What about this?  Is there something I need to do to the filesystem?  Feeling very sheepish, as I'm sure the answer is obvious and I'm just not seeing it.

```
johnw@johnw-desktop:/media/Raid$ df -h .
Filesystem      Size  Used Avail Use% Mounted on
/dev/md5        [COLOR=#ff0000]1.8T[/COLOR]  842G  900G  49% /media/Raid

```
[IMG]http://i28.photobucket.com/albums/c233/weirich_j/Screenshotfrom2014-01-14221623.png[/IMG]

---

### Post by rubylaser on 2014-01-15
No need to feel sheepish, it was a great question :) Assuming you aren't using LVM on top of your array, to take advantage of the new space, you need to resize your filesystem.  Open a terminal and run these.
```

sudo -i
umount /media/Raid
fsck.ext4 -f /dev/md5
resize2fs /dev/md5
mount -a
exit
df -h | grep md5

```

---

