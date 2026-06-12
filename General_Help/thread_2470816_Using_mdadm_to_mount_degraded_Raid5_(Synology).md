---
title: "Using mdadm to mount degraded Raid5 (Synology)"
date: 2022-01-12
forum: General Help
---

### Post by eicen2 on 2022-01-12
Hi!

4 years back, I had a Synology raid, die on me. 
I only remember that 1 disk died first, and I believe I tried to rebuild the raid, and in that process one more disc stopped working. 
I'm not sure.. but I gave up on the project, and stored the diskstation and the disks away. 

I had a lot of important personal files on that NAS - not at least all the pictures from my sons name giving party, which I would love to get back. 

Recently I learned that maybe it could be possible to mount the degraded raid on a ubuntu system, and get access to the lost files?
I have googled a lot, and tried following some guides, and descriptions from other guys, having sort of the same issue.
Tried to follow this guide, with no luck: [https://kb.synology.com/en-my/DSM/tutorial/How_can_I_recover_data_from_my_DiskStation_using_a_PC](https://kb.synology.com/en-my/DSM/tutorial/How_can_I_recover_data_from_my_DiskStation_using_a_PC)

I am not that "pro" regarding linux, and maybe I'm missing some obvious details - so I hope that you guys would help me in the right direction.


First of.. 
The raid was a 4 disk RAID5 - I have 5 disks (I think the extra 1, is the one I changed)
I have all 5 disks connected: /dev/sda, /dev/sdb, /dev/sdc, /dev/sdd, /dev/sdf, 
When running a 'mdadm --examine /dev/sd*' it looks like there was 6 disks: 

'mdadm --examine /dev/sd*' (/dev/sde is the ubuntu system disk)
```
root@kenneth-P5K:~# mdadm --examine /dev/sd*
mdmon: /dev/sda is not attached to Intel(R) RAID controller.
mdmon: /dev/sda is not attached to Intel(R) RAID controller.
/dev/sda:
          Magic : Intel Raid ISM Cfg Sig.
        Version : 1.3.00
    Orig Family : ab2964f9
         Family : ab2ca407
     Generation : 000006a2
     Attributes : All supported
           UUID : 02fa2522:50f13fd6:7c364353:bc056c13
       Checksum : f0f730ec correct
    MPB Sectors : 2
          Disks : 6
   RAID Devices : 1

  Disk02 Serial : WD-WCAZA1995887
          State : active
             Id : 00020000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)

[Raid]:
           UUID : b039b833:7cf78f18:0e56ba97:8c360789
     RAID Level : 5 <-- 5
        Members : 6 <-- 6
          Slots : [UUUUUU] <-- [UUUU_U]
    Failed disk : none
      This Slot : 2
     Array Size : 19339724800 (9221.90 GiB 9901.94 GB)
   Per Dev Size : 3867945224 (1844.38 GiB 1980.39 GB)
  Sector Offset : 0
    Num Stripes : 15109160
     Chunk Size : 128 KiB <-- 128 KiB
       Reserved : 0
  Migrate State : rebuild
      Map State : normal <-- degraded
     Checkpoint : 2122 (256)
    Dirty State : clean

  Disk00 Serial : WD-WCAZA1904166
          State : active
             Id : 00000000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)

  Disk01 Serial : WD-WCAZA1995841
          State : active
             Id : 00010000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)

  Disk03 Serial : WD-WCAZA1946337
          State : active
             Id : 00030000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)

  Disk04 Serial : WD-WCAZA1996154
          State : active
             Id : 00040000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)

  Disk05 Serial : WD-WCAZA1890001
          State : active
             Id : 00050000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)
mdmon: /dev/sdb is not attached to Intel(R) RAID controller.
mdmon: /dev/sdb is not attached to Intel(R) RAID controller.
/dev/sdb:
          Magic : Intel Raid ISM Cfg Sig.
        Version : 1.3.00
    Orig Family : ab2964f9
         Family : ab2ca407
     Generation : 000006a2
     Attributes : All supported
           UUID : 02fa2522:50f13fd6:7c364353:bc056c13
       Checksum : f0f730ec correct
    MPB Sectors : 2
          Disks : 6
   RAID Devices : 1

  Disk04 Serial : WD-WCAZA1996154
          State : active
             Id : 00040000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)

[Raid]:
           UUID : b039b833:7cf78f18:0e56ba97:8c360789
     RAID Level : 5 <-- 5
        Members : 6 <-- 6
          Slots : [UUUUUU] <-- [UUUU_U]
    Failed disk : none
      This Slot : 4 (out-of-sync)
     Array Size : 19339724800 (9221.90 GiB 9901.94 GB)
   Per Dev Size : 3867945224 (1844.38 GiB 1980.39 GB)
  Sector Offset : 0
    Num Stripes : 15109160
     Chunk Size : 128 KiB <-- 128 KiB
       Reserved : 0
  Migrate State : rebuild
      Map State : normal <-- degraded
     Checkpoint : 2122 (256)
    Dirty State : clean

  Disk00 Serial : WD-WCAZA1904166
          State : active
             Id : 00000000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)

  Disk01 Serial : WD-WCAZA1995841
          State : active
             Id : 00010000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)

  Disk02 Serial : WD-WCAZA1995887
          State : active
             Id : 00020000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)

  Disk03 Serial : WD-WCAZA1946337
          State : active
             Id : 00030000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)

  Disk05 Serial : WD-WCAZA1890001
          State : active
             Id : 00050000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)
mdmon: /dev/sdc is not attached to Intel(R) RAID controller.
mdmon: /dev/sdc is not attached to Intel(R) RAID controller.
/dev/sdc:
          Magic : Intel Raid ISM Cfg Sig.
        Version : 1.3.00
    Orig Family : ab2964f9
         Family : ab2ca407
     Generation : 000006a2
     Attributes : All supported
           UUID : 02fa2522:50f13fd6:7c364353:bc056c13
       Checksum : f0f730ec correct
    MPB Sectors : 2
          Disks : 6
   RAID Devices : 1

  Disk03 Serial : WD-WCAZA1946337
          State : active
             Id : 00030000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)

[Raid]:
           UUID : b039b833:7cf78f18:0e56ba97:8c360789
     RAID Level : 5 <-- 5
        Members : 6 <-- 6
          Slots : [UUUUUU] <-- [UUUU_U]
    Failed disk : none
      This Slot : 3
     Array Size : 19339724800 (9221.90 GiB 9901.94 GB)
   Per Dev Size : 3867945224 (1844.38 GiB 1980.39 GB)
  Sector Offset : 0
    Num Stripes : 15109160
     Chunk Size : 128 KiB <-- 128 KiB
       Reserved : 0
  Migrate State : rebuild
      Map State : normal <-- degraded
     Checkpoint : 2122 (256)
    Dirty State : clean

  Disk00 Serial : WD-WCAZA1904166
          State : active
             Id : 00000000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)

  Disk01 Serial : WD-WCAZA1995841
          State : active
             Id : 00010000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)

  Disk02 Serial : WD-WCAZA1995887
          State : active
             Id : 00020000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)

  Disk04 Serial : WD-WCAZA1996154
          State : active
             Id : 00040000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)

  Disk05 Serial : WD-WCAZA1890001
          State : active
             Id : 00050000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)
mdmon: /dev/sdd is not attached to Intel(R) RAID controller.
mdmon: /dev/sdd is not attached to Intel(R) RAID controller.
/dev/sdd:
          Magic : Intel Raid ISM Cfg Sig.
        Version : 1.3.00
    Orig Family : ab2964f9
         Family : ab2ca407
     Generation : 000006a2
     Attributes : All supported
           UUID : 02fa2522:50f13fd6:7c364353:bc056c13
       Checksum : f0f730ec correct
    MPB Sectors : 2
          Disks : 6
   RAID Devices : 1

  Disk00 Serial : WD-WCAZA1904166
          State : active
             Id : 00000000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)

[Raid]:
           UUID : b039b833:7cf78f18:0e56ba97:8c360789
     RAID Level : 5 <-- 5
        Members : 6 <-- 6
          Slots : [UUUUUU] <-- [UUUU_U]
    Failed disk : none
      This Slot : 0
     Array Size : 19339724800 (9221.90 GiB 9901.94 GB)
   Per Dev Size : 3867945224 (1844.38 GiB 1980.39 GB)
  Sector Offset : 0
    Num Stripes : 15109160
     Chunk Size : 128 KiB <-- 128 KiB
       Reserved : 0
  Migrate State : rebuild
      Map State : normal <-- degraded
     Checkpoint : 2122 (256)
    Dirty State : clean

  Disk01 Serial : WD-WCAZA1995841
          State : active
             Id : 00010000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)

  Disk02 Serial : WD-WCAZA1995887
          State : active
             Id : 00020000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)

  Disk03 Serial : WD-WCAZA1946337
          State : active
             Id : 00030000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)

  Disk04 Serial : WD-WCAZA1996154
          State : active
             Id : 00040000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)

  Disk05 Serial : WD-WCAZA1890001
          State : active
             Id : 00050000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)
/dev/sde:
   MBR Magic : aa55
Partition[0] :    959993856 sectors at         2048 (type 83)
Partition[1] :     16773122 sectors at    959997950 (type 05)
mdadm: No md superblock detected on /dev/sde1.
/dev/sde2:
   MBR Magic : aa55
Partition[0] :     16773120 sectors at            2 (type 82)
mdadm: No md superblock detected on /dev/sde5.
mdmon: /dev/sdf is not attached to Intel(R) RAID controller.
mdmon: /dev/sdf is not attached to Intel(R) RAID controller.
/dev/sdf:
          Magic : Intel Raid ISM Cfg Sig.
        Version : 1.3.00
    Orig Family : ab2964f9
         Family : ab2ca407
     Generation : 000006a2
     Attributes : All supported
           UUID : 02fa2522:50f13fd6:7c364353:bc056c13
       Checksum : f0f730ec correct
    MPB Sectors : 2
          Disks : 6
   RAID Devices : 1

  Disk01 Serial : WD-WCAZA1995841
          State : active
             Id : 00010000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)

[Raid]:
           UUID : b039b833:7cf78f18:0e56ba97:8c360789
     RAID Level : 5 <-- 5
        Members : 6 <-- 6
          Slots : [UUUUUU] <-- [UUUU_U]
    Failed disk : none
      This Slot : 1
     Array Size : 19339724800 (9221.90 GiB 9901.94 GB)
   Per Dev Size : 3867945224 (1844.38 GiB 1980.39 GB)
  Sector Offset : 0
    Num Stripes : 15109160
     Chunk Size : 128 KiB <-- 128 KiB
       Reserved : 0
  Migrate State : rebuild
      Map State : normal <-- degraded
     Checkpoint : 2122 (256)
    Dirty State : clean

  Disk00 Serial : WD-WCAZA1904166
          State : active
             Id : 00000000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)

  Disk02 Serial : WD-WCAZA1995887
          State : active
             Id : 00020000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)

  Disk03 Serial : WD-WCAZA1946337
          State : active
             Id : 00030000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)

  Disk04 Serial : WD-WCAZA1996154
          State : active
             Id : 00040000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)

  Disk05 Serial : WD-WCAZA1890001
          State : active
             Id : 00050000
    Usable Size : 3907022862 (1863.01 GiB 2000.40 GB)
```


I don't think I have the disk with the serial: WD-WCAZA1890001 - even if a did have the disk, I am pretty sure that it was never a part of the raid. 
Do you think I could work without ?

I have no real experience working with raids, so I really don't know what to look for.. 

I'm just gonna parse some commands here: 

'fdisk -l /dev/sd*' (it doesn't look like /dev/sdb has the same partition table?)
```
root@kenneth-P5K:~# fdisk -l /dev/sd*
Disk /dev/sda: 1,8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0009fc73

Enhed      Opstart   Start       ****   Sektorer  Size Id Type
/dev/sda1              256    4980735    4980480  2,4G fd Linux raid autodetekt
/dev/sda2          4980736    9175039    4194304    2G fd Linux raid autodetekt
/dev/sda3          9437184 3907015007 3897577824  1,8T  f W95 udvidet (LBA)
/dev/sda5          9453280 3907015007 3897561728  1,8T fd Linux raid autodetekt
Disk /dev/sdb: 1,8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sdc: 1,8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00025662

Enhed      Opstart   Start       ****   Sektorer  Size Id Type
/dev/sdc1              256    4980735    4980480  2,4G fd Linux raid autodetekt
/dev/sdc2          4980736    9175039    4194304    2G fd Linux raid autodetekt
/dev/sdc3          9437184 3907015007 3897577824  1,8T  f W95 udvidet (LBA)
/dev/sdc5          9453280 3907015007 3897561728  1,8T fd Linux raid autodetekt
Disk /dev/sdd: 1,8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0002dd6d

Enhed      Opstart   Start       ****   Sektorer  Size Id Type
/dev/sdd1              256    4980735    4980480  2,4G fd Linux raid autodetekt
/dev/sdd2          4980736    9175039    4194304    2G fd Linux raid autodetekt
/dev/sdd3          9437184 3907015007 3897577824  1,8T  f W95 udvidet (LBA)
/dev/sdd5          9453280 3907015007 3897561728  1,8T fd Linux raid autodetekt
Disk /dev/sde: 465,8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x9150ded1

Enhed      Opstart     Start      ****  Sektorer   Size Id Type
/dev/sde1  *            2048 959995903 959993856 457,8G 83 Linux
/dev/sde2          959997950 976771071  16773122     8G  5 Udvidet
/dev/sde5          959997952 976771071  16773120     8G 82 Linux swap / Solaris

Partition 2 does not start on physical sector boundary.
Disk /dev/sde1: 457,8 GiB, 491516854272 bytes, 959993856 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk /dev/sde2: 1 KiB, 1024 bytes, 2 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Alignment offset: 1024 bytes
Disklabel type: dos
Disk identifier: 0x134b7ed1

Enhed       Opstart Start     **** Sektorer Size Id Type
/dev/sde2p1             2 16773121 16773120   8G 82 Linux swap / Solaris
Disk /dev/sde5: 8 GiB, 8587837440 bytes, 16773120 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk /dev/sdf: 1,8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000ea65d

Enhed      Opstart   Start       ****   Sektorer  Size Id Type
/dev/sdf1              256    4980735    4980480  2,4G fd Linux raid autodetekt
/dev/sdf2          4980736    9175039    4194304    2G fd Linux raid autodetekt
/dev/sdf3          9437184 3907015007 3897577824  1,8T  f W95 udvidet (LBA)
/dev/sdf5          9453280 3907015007 3897561728  1,8T fd Linux raid autodetekt
```

'cat /proc/mdstat'
```
root@kenneth-P5K:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md126 : inactive sdd[4] sdf[3] sda[2] sdc[1] sdb[0]
      9669863060 blocks super external:/md127/0
       
md127 : inactive sda[4](S) sdb[3](S) sdd[2](S) sdc[1](S) sdf[0](S)
      15765 blocks super external:imsm
       
unused devices: <none>

```

I hope it makes sense to some of you?

---

