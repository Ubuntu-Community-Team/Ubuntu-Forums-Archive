---
title: "Rebuilding Array with mdadm after OS Reinstallation"
date: 2015-08-24
forum: General Help
---

### Post by stevoo on 2015-08-24
Hi Everyone,

I have lost my main server OS and proceeded with installing Ubuntu server 15.04 on a new hard disk.

I have a Raid [5] using mdadm which i cant seem to be able to rebuild correctly.

My fdisk -l returns this

```

Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xde5e7da5

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdb1  *       63 1953520064 1953520002 931.5G fd Linux raid autodetect

Partition 2 does not start on physical sector boundary.


Disk /dev/sda: 3.7 TiB, 4000785948160 bytes, 7814035055 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start        End    Sectors   Size Id Type
/dev/sda1          63 1953520064 1953520002 931.5G fd Linux raid autodetect

Partition 2 does not start on physical sector boundary.


Disk /dev/sdc: 931.5 GiB, 1000203804160 bytes, 1953523055 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xa839bd05

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdc1          63 1953520064 1953520002 931.5G fd Linux raid autodetect

Disk /dev/sde: 111.8 GiB, 120033041920 bytes, 234439535 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x851e8e95

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sde1            2048 230772735 230770688  110G 83 Linux
/dev/sde2       230774782 234438655   3663874  1.8G  5 Extended
/dev/sde5       230774784 234438655   3663872  1.8G 82 Linux swap / Solaris

Disk /dev/sdd: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x7dce341f

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdd1  *       63 1953520064 1953520002 931.5G fd Linux raid autodetect

```

We can see that the disks on sd[a-d] are my Linux Raid


```

$ sudo mdadm --examine /dev/sda
/dev/sda:
   MBR Magic : aa55
Partition[0] :   1953520002 sectors at           63 (type fd)
sudo mdadm --examine /dev/sdb
/dev/sdb:
   MBR Magic : aa55
Partition[0] :   1953520002 sectors at           63 (type fd)
$ sudo mdadm --examine /dev/sdc
/dev/sdc:
   MBR Magic : aa55
Partition[0] :   1953520002 sectors at           63 (type fd)
$ sudo mdadm --examine /dev/sdd
/dev/sdd:
          Magic : a92b4efc
        Version : 0.91.00
           UUID : 99b483b8:48ee096e:31d25ca3:d1d8350e
  Creation Time : Fri Mar 11 10:43:57 2011
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 2930279808 (2794.53 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

  Reshape pos'n : 9283008 (8.85 GiB 9.51 GB)
  Delta Devices : 1 (3->4)

    Update Time : Mon Mar 14 11:09:11 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 65c5a664 - correct
         Events : 362

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       64        3      active sync   /dev/sde

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync
   3     3       8       64        3      active sync   /dev/sde


```


Restarting my pc will automatically create a /dev/md127 which i can assume comes wrong from the wrong type in my sdd

Any ideas how can i recreate my array correctly ? 


Doing a create will create my array . Notice that i cannot find the sdd1 ! In this case i have used the sdd 
```
$ sudo mdadm --create --assume-clean --level=5 --raid-devices=4 --verbose /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 512K
mdadm: /dev/sda1 appears to be part of a raid array:
       level=raid5 devices=3 ctime=Mon Aug 24 10:20:35 2015
mdadm: /dev/sdb1 appears to be part of a raid array:
       level=raid5 devices=3 ctime=Mon Aug 24 10:20:35 2015
mdadm: /dev/sdc1 appears to be part of a raid array:
       level=raid5 devices=3 ctime=Mon Aug 24 10:20:35 2015
mdadm: /dev/sdd appears to be part of a raid array:
       level=raid5 devices=4 ctime=Fri Mar 11 10:43:57 2011
mdadm: partition table exists on /dev/sdd but will be lost or
       meaningless after creating array
mdadm: size set to 976628736K
mdadm: automatically enabling write-intent bitmap on large array
Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.

```

and my /cat/proc
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdd[3] sdc1[2] sdb1[1] sda1[0]
      2929886208 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      bitmap: 0/8 pages [0KB], 65536KB chunk

```

```
$dmesg | tail
[  829.686070]  --- level:5 rd:4 wd:4
[  829.686075]  disk 0, o:1, dev:sda1
[  829.686079]  disk 1, o:1, dev:sdb1
[  829.686083]  disk 2, o:1, dev:sdc1
[  829.686087]  disk 3, o:1, dev:sdd
[  829.686120] md0: Warning: Device sdb1 is misaligned
[  829.686327] created bitmap (8 pages) for device md0
[  829.688196] md0: bitmap initialized from disk: read 1 pages, set 14903 of 14903 bits
[  829.781805] md0: detected capacity change from 0 to 3000203476992
[  829.786066]  md0: unknown partition table

```



Any ideas on how can i proceed ?

---

### Post by stevoo on 2015-08-25
```
$ sudo file -s /dev/sda
/dev/sda: ; partition 1 : ID=0xfd, start-CHS (0x0,1,1), end-CHS (0x3ff,254,63), startsector 63, 1953520002 sectors
$ sudo file -s /dev/sdb
/dev/sdb: DOS/MBR boot sector
$ sudo file -s /dev/sdc
/dev/sdc: ; partition 1 : ID=0xfd, start-CHS (0x0,1,1), end-CHS (0x3ff,254,63), startsector 63, 1953520002 sectors, extended partition table (last)\011
$ sudo file -s /dev/sdd
/dev/sdd: , extended partition table (last)\011
$ sudo file -s /dev/sda1
/dev/sda1: Linux Software RAID version 1.2 (1) UUID=7ac78caf:2cf61d96: 6dfa50c:fa5832a7 name=Stelios-Home:0 level=5 disks=4
$ sudo file -s /dev/sdb1
/dev/sdb1: SGI XFS filesystem data (blksz 4096, inosz 256, v2 dirs)
$ sudo file -s /dev/sdc1
/dev/sdc1: Linux Software RAID version 1.2 (1) UUID=7ac78caf:2cf61d96: 6dfa50c:fa5832a7 name=Stelios-Home:0 level=5 disks=4
$ sudo file -s /dev/sdd1
/dev/sdd1: Linux Software RAID version 1.2 (1) UUID=7ac78caf:2cf61d96: 6dfa50c:fa5832a7 name=Stelios-Home:0 level=5 disks=4

```


Apparently my disks seem to be all over the place.




so i did an XFS_check

```
$sudo xfs_repair -n -v /dev/sda1
Phase 1 - find and verify superblock...
bad primary superblock - bad magic number !!!

attempting to find secondary superblock...

```


```
$ sudo xfs_repair -n -v /dev/sdb1
Phase 1 - find and verify superblock...
error reading superblock 17 -- seek to offset 1062714671104 failed
couldn't verify primary superblock - attempted to perform I/O beyond EOF !!!

attempting to find secondary superblock...


```

```
$ sudo xfs_repair -n -v /dev/sdc1
Phase 1 - find and verify superblock...
bad primary superblock - bad magic number !!!

attempting to find secondary superblock...

```

```

$ sudo xfs_repair -n -v /dev/sdd1
Phase 1 - find and verify superblock...
bad primary superblock - bad magic number !!!

attempting to find secondary superblock...

```

Apparently, there are no superblocks for my raid.... 
Anyone know how i can proceed safely ?

---

### Post by stevoo on 2015-08-26
*bump*
Still scratching my self for a solution .... 

doing a vgscan will get me this 

```
steliosph@Stelios-Home:~$ sudo vgscan -d -v
    DEGRADED MODE. Incomplete RAID LVs will be processed.
    Wiping cache of LVM-capable devices
    Wiping internal VG cache
  Reading all physical volumes.  This may take a while...
    Finding all volume groups
  No volume groups found

```


```

steliosph@Stelios-Home:~$ sudo mdadm --assemble --scan -v /dev/md0
mdadm: looking for devices for /dev/md0
mdadm: no RAID superblock on /dev/sde5
mdadm: no RAID superblock on /dev/sde2
mdadm: no RAID superblock on /dev/sde1
mdadm: no RAID superblock on /dev/sde
mdadm: /dev/sdd1 has wrong uuid.
mdadm: /dev/sdc1 has wrong uuid.
mdadm: no RAID superblock on /dev/sdc
mdadm: /dev/sdb1 has wrong uuid.
mdadm: no RAID superblock on /dev/sdb
mdadm: /dev/sda1 has wrong uuid.
mdadm: no RAID superblock on /dev/sda
mdadm: /dev/sdd is identified as a member of /dev/md0, slot 3.
mdadm: no uptodate device for slot 0 of /dev/md0
mdadm: no uptodate device for slot 2 of /dev/md0
mdadm: no uptodate device for slot 4 of /dev/md0
mdadm: added /dev/sdd to /dev/md0 as 3
mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.

```


** Edit 

So i removed the /etc/mdadm/mdadm.conf and executed the command again
```

steliosph@Stelios-Home:~$ sudo mdadm --assemble --scan -v
mdadm: looking for devices for further assembly
mdadm: no recogniseable superblock on /dev/sde5
mdadm: Cannot assemble mbr metadata on /dev/sde2
mdadm: no recogniseable superblock on /dev/sde1
mdadm: Cannot assemble mbr metadata on /dev/sde
mdadm: no RAID superblock on /dev/sdc
mdadm: no RAID superblock on /dev/sdb
mdadm: no RAID superblock on /dev/sda
mdadm: /dev/sdd1 is identified as a member of /dev/md/0, slot 3.
mdadm: /dev/sdc1 is identified as a member of /dev/md/0, slot 2.
mdadm: /dev/sdb1 is identified as a member of /dev/md/0, slot 1.
mdadm: /dev/sda1 is identified as a member of /dev/md/0, slot 0.
mdadm: added /dev/sdb1 to /dev/md/0 as 1
mdadm: added /dev/sdc1 to /dev/md/0 as 2
mdadm: added /dev/sdd1 to /dev/md/0 as 3
mdadm: added /dev/sda1 to /dev/md/0 as 0
mdadm: /dev/md/0 has been started with 4 drives.

```

So it found the array (again and started it )
No rebuilding in cat


But still cant mount the array



Just found this . Is the MBR broken on the disks .. should i figure out how to fix that ? 
Why is it correct on [1] ? 


```

$ sudo mdadm -E /dev/sd[abcd]
/dev/sda:
   MBR Magic : aa55
Partition[0] :   1953520002 sectors at           63 (type fd)
/dev/sdb:
   MBR Magic : aa55
Partition[0] :   1953520002 sectors at           63 (type fd)
/dev/sdc:
   MBR Magic : aa55
Partition[0] :   1953520002 sectors at           63 (type fd)
/dev/sdd:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : dc451dc2:5ef48d0d:71430fe5:21f04e96
           Name : Stelios-Home:0  (local to host Stelios-Home)
  Creation Time : Mon Aug 24 10:38:39 2015
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 1953263024 (931.39 GiB 1000.07 GB)
     Array Size : 2929886208 (2794.16 GiB 3000.20 GB)
  Used Dev Size : 1953257472 (931.39 GiB 1000.07 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=5552 sectors
          State : clean
    Device UUID : 782012dc:32181988:6ef055ae:93a87d3a

Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Aug 24 10:38:39 2015
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : d5187050 - correct
         Events : 0

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)

```


```

$ sudo mdadm -E /dev/sd[abcd]
/dev/sda:
   MBR Magic : aa55
Partition[0] :   1953520002 sectors at           63 (type fd)
/dev/sdb:
   MBR Magic : aa55
Partition[0] :   1953520002 sectors at           63 (type fd)
/dev/sdc:
   MBR Magic : aa55
Partition[0] :   1953520002 sectors at           63 (type fd)
/dev/sdd:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : dc451dc2:5ef48d0d:71430fe5:21f04e96
           Name : Stelios-Home:0  (local to host Stelios-Home)
  Creation Time : Mon Aug 24 10:38:39 2015
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 1953263024 (931.39 GiB 1000.07 GB)
     Array Size : 2929886208 (2794.16 GiB 3000.20 GB)
  Used Dev Size : 1953257472 (931.39 GiB 1000.07 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=5552 sectors
          State : clean
    Device UUID : 782012dc:32181988:6ef055ae:93a87d3a

Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Aug 24 10:38:39 2015
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : d5187050 - correct
         Events : 0

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)

```



Another edit perhaps someone has any idea
 sfdisk -d /dev/sd[abcd]
Why is sdb bootable ? 

```

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=1953520002, Id=fd
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=1953520002, Id=fd, bootable
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
# partition table of /dev/sdc
unit: sectors

/dev/sdc1 : start=       63, size=1953520002, Id=fd
/dev/sdc2 : start=        0, size=        0, Id= 0
/dev/sdc3 : start=        0, size=        0, Id= 0
/dev/sdc4 : start=        0, size=        0, Id= 0
# partition table of /dev/sdd
unit: sectors

/dev/sdd1 : start=       63, size=1953520002, Id=fd
/dev/sdd2 : start=        0, size=        0, Id= 0
/dev/sdd3 : start=        0, size=        0, Id= 0
/dev/sdd4 : start=        0, size=        0, Id= 0


```

---

