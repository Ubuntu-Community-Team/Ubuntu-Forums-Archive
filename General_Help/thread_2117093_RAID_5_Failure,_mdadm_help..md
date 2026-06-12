---
title: "RAID 5 Failure, mdadm help."
date: 2013-02-17
forum: General Help
---

### Post by xlr8ed on 2013-02-17
I have two RAID arrays, 
1 RAID 5 array with 4 - 2TB disks(/dev/md0 /dev/sdf /dev/sdg /dev/sdh /dev/sdi) 
1 RAID 0 array with 2 - 3TB disks(/dev/md1 /dev/sdb /dev/sdc)

After a reboot, I ended up with this.

Help needed, as I have about 4 TB of data on MD0 that, while I can recover most of it, would take a very very long time.


> 
root@Grover:/# cat /proc/mdstat
Personalities : [raid0]
md1 : active raid0 sdb[0] sdc[1]
      5860533152 blocks super 1.2 4k chunks

unused devices: <none>
root@Grover:/#


Fdisk -l
> 
root@Grover:/# fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a6279

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   488396799   244197376   83  Linux

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  4294967295  2147483647+  ee  GPT

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63  1953520064   976760001   83  Linux

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63  1953520064   976760001   83  Linux

WARNING: GPT (GUID Partition Table) detected on '/dev/sdf'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1  3907029167  1953514583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdg'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdg: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1  3907029167  1953514583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdh'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdh: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1  3907029167  1953514583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdi'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdi: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1  3907029167  1953514583+  ee  GPT

Disk /dev/md1: 6001.2 GB, 6001185947648 bytes
2 heads, 4 sectors/track, 1465133288 cylinders, total 11721066304 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 4096 bytes / 8192 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table
root@Grover:/#


mdadm.conf
> 
root@Grover:/# cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=55d319cd:6d8df947:81c22369:2d990135 name=Grover:0

# This file was auto-generated on Fri, 01 Feb 2013 20:23:25 -0600
# by mkconf $Id$
DEVICE /dev/sdb /dev/sdc
ARRAY /dev/md1 level=raid0 devices=/dev/sdb,/dev/sdc


mdadm --examine
> 
root@Grover:/# mdadm --examine /dev/sdf
/dev/sdf:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)


root@Grover:/# mdadm --examine /dev/sdg
/dev/sdg:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)


root@Grover:/# mdadm --examine /dev/sdh
/dev/sdh:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 55d319cd:6d8df947:81c22369:2d990135
           Name : Grover:0  (local to host Grover)
  Creation Time : Sat Oct 22 12:45:24 2011
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3907025072 (1863.01 GiB 2000.40 GB)
     Array Size : 5860536576 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 3907024384 (1863.01 GiB 2000.40 GB)
    Data Offset : 4096 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 799868b4:57b6c66d:811e4371:c04afe9a

    Update Time : Sun Feb 17 11:21:59 2013
       Checksum : a249e558 - correct
         Events : 10673

         Layout : left-symmetric
     Chunk Size : 128K

   Device Role : Active device 0
   Array State : AAAA ('A' == active, '.' == missing)


root@Grover:/# mdadm --examine /dev/sdi
/dev/sdi:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)


mdadm --misc --detail 
> 
root@Grover:/# mdadm --misc --detail /dev/md0
mdadm: cannot open /dev/md0: No such file or directory

root@Grover:/# mdadm -E /dev/sdf1
mdadm: No md superblock detected on /dev/sdf1.

root@Grover:/# mdadm -E /dev/sdg1
mdadm: No md superblock detected on /dev/sdg1.

root@Grover:/# mdadm -E /dev/sdh1
mdadm: cannot open /dev/sdh1: No such file or directory

root@Grover:/# mdadm -E /dev/sdi1
mdadm: No md superblock detected on /dev/sdi1.
root@Grover:/#


Huh?
> 
root@Grover:/# mdadm -D /dev/md0
mdadm: cannot open /dev/md0: No such file or directory
root@Grover:/#



Attempting to Rebuild
> 
root@Grover:/# mdadm --verbose --assemble --force /dev/md0 /dev/sdf1 /dev/sdg1 /dev/sdh1 /dev/sdi1
mdadm: looking for devices for /dev/md0
mdadm: no recogniseable superblock on /dev/sdf1
mdadm: /dev/sdf1 has no superblock - assembly aborted
root@Grover:/#


---

### Post by SaturnusDJ on 2013-02-18
I think the output of 
```
mdadm --examine /dev/sdh
```
is a bit strange.

This output is only expected for
```
mdadm --examine /dev/sdh1
```


Please post the exact output for the following
```
mdadm --examine /dev/sd[f-i]
```

And
```
mdadm --examine /dev/sd[f-i]1
```

---

