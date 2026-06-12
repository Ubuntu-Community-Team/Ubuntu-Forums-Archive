---
title: "RAID6 Array MDADM Assemble Force Not Working Out of date?"
date: 2018-12-02
forum: General Help
---

### Post by t4nd4r on 2018-12-02
[COLOR=#242729][FONT=Arial][FONT=inherit]Hello,[/FONT]
[/FONT][/COLOR][COLOR=#242729][FONT=Arial][FONT=inherit]
I hope someone has clear guidance on what to do next!

Somehow I got into a situation where the RAID6 went inactive, following some Googlefoo I stopped it /dev/md0[/FONT]
[FONT=inherit]Now, I can't get the RAID6 to assemble!
[/FONT]
> ryan:~$ sudo mdadm --verbose --assemble --force /dev/md0 /dev/sd[fdbkigeclajh]
mdadm: looking for devices for /dev/md0
mdadm: /dev/sda is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sdb is identified as a member of /dev/md0, slot 7.
mdadm: /dev/sdc is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdd is identified as a member of /dev/md0, slot 3.
mdadm: /dev/sde is identified as a member of /dev/md0, slot 4.
mdadm: /dev/sdf is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdg is identified as a member of /dev/md0, slot 6.
mdadm: /dev/sdh is identified as a member of /dev/md0, slot 9.
mdadm: /dev/sdi is identified as a member of /dev/md0, slot 5.
mdadm: /dev/sdj is identified as a member of /dev/md0, slot 11.
mdadm: /dev/sdk is identified as a member of /dev/md0, slot 10.
mdadm: /dev/sdl is identified as a member of /dev/md0, slot 8.
mdadm: added /dev/sdc to /dev/md0 as 1
mdadm: added /dev/sda to /dev/md0 as 2
mdadm: added /dev/sdd to /dev/md0 as 3
mdadm: added /dev/sde to /dev/md0 as 4
mdadm: added /dev/sdi to /dev/md0 as 5
mdadm: added /dev/sdg to /dev/md0 as 6
mdadm: added /dev/sdb to /dev/md0 as 7
mdadm: added /dev/sdl to /dev/md0 as 8 (possibly out of date)
mdadm: added /dev/sdh to /dev/md0 as 9
mdadm: added /dev/sdk to /dev/md0 as 10 (possibly out of date)
mdadm: added /dev/sdj to /dev/md0 as 11 (possibly out of date)
mdadm: added /dev/sdf to /dev/md0 as 0
mdadm: /dev/md0 assembled from 9 drives - not enough to start the array.

[FONT=inherit]I've examined every drive and they are all clean. I can't figure out the "possibly out of date".[/FONT]
[FONT=inherit]My next step I was going to try is creating the array again using the --assume-clean tag... but I want to be positive that's what I should do? Also, the order would be important and I would start with slot 0 going up to slot 11?[/FONT]
[FONT=inherit]I also checked the Data Offset information and they all match up with each other.[/FONT]
[FONT=inherit]Thanks for any info![/FONT]

[/FONT][/COLOR]

---

### Post by darkod on 2018-12-02
You have one more option before trying to recreate with --assume-clean.

To your above command add --run. That will try to run it even though some members show out of date. That refers to the Events counter. You can compare Events of each member by using:
```
sudo mdadm -E /dev/sd[abcd...]
```

You can do that first if you want to see the info before trying the assemble with --run.

---

### Post by t4nd4r on 2018-12-02
Unfortunately, I did the command before waiting for your input.

I'm now sitting staring at a new problem. The partition appears corrupt after the assume-clean? It also changed from md0 to md127

What can I do from here? I can't mount it due to 



ryan:/home$ sudo mount /dev/md127 /media
mount: /dev/md127: can't read superblock

Disk information... I hope I didn't bork something up :/

All the 3.7 TiB drives should be in the same RAID6 array.

```
ryan:/home$ sudo fdisk -l
Disk /dev/sdb: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/sda: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




The primary GPT table is corrupt, but the backup appears OK, so that will be used.
Disk /dev/sdc: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: B7AE4F43-A334-4632-8FE0-A4DC6324C7CE




Disk /dev/sdd: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




The primary GPT table is corrupt, but the backup appears OK, so that will be used.
Disk /dev/sdf: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: AAEACDED-333E-4231-9419-5FF4EBF5A0F8




Disk /dev/sde: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/sdh: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/sdg: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/sdq: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xab7135f3


Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdq1  *         2048 960163839 960161792 457.9G 83 Linux
/dev/sdq2       960165886 976771071  16605186   7.9G  5 Extended
/dev/sdq5       960165888 976771071  16605184   7.9G 82 Linux swap / Solaris




Disk /dev/sdm: 7.3 TiB, 8001563222016 bytes, 15628053168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/sdn: 7.3 TiB, 8001563222016 bytes, 15628053168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/sdp: 7.3 TiB, 8001563222016 bytes, 15628053168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/sdo: 7.3 TiB, 8001563222016 bytes, 15628053168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/sdi: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/sdj: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/sdk: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/sdl: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




The primary GPT table is corrupt, but the backup appears OK, so that will be used.
Disk /dev/sdr: 7.3 TiB, 8001563222016 bytes, 15628053168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 89F323B6-31C0-49BE-9F69-FE2B09EAE1B9


Device     Start         End     Sectors  Size Type
/dev/sdr1   2048 15628050431 15628048384  7.3T Microsoft basic data




Disk /dev/sds: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x00000000


Device     Boot Start       End   Sectors   Size Id Type
/dev/sds1           2 732566645 732566644 349.3G af HFS / HFS+


Partition 1 does not start on physical sector boundary.




Disk /dev/sdt: 7.3 TiB, 8001563222016 bytes, 15628053168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x16f2a91f


Device     Boot Start        End    Sectors Size Id Type
/dev/sdt1           1 4294967295 4294967295   2T ee GPT


Partition 1 does not start on physical sector boundary.




Disk /dev/sdu: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/md3: 29.1 TiB, 32005714608128 bytes, 62511161344 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 524288 bytes / 2097152 bytes




Disk /dev/md2: 2.7 TiB, 3000458739712 bytes, 5860270976 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes



```

Here is the command I used prior to your comment.

```

sudo mdadm --create --assume-clean --level=6 --raid-devices=12 /dev/md0 /dev/sdf /dev/sdc /dev/sda /dev/sdd /dev/sde /dev/sdi /dev/sdg /dev/sdb /dev/sdl /dev/sdh /dev/sdk /dev/sdj
```

I based the order off the "Device role:"

```

ryan:~$ sudo mdadm --examine /dev/sd[fdbkigeclajh]
/dev/sda:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 569f899d:8bed5eee:2d47c23f:33b2b337
           Name : TandarLinux:0  (local to host TandarLinux)
  Creation Time : Thu Jun  2 21:06:49 2016
     Raid Level : raid6
   Raid Devices : 12


 Avail Dev Size : 7813874352 (3725.95 GiB 4000.70 GB)
     Array Size : 39068871680 (37258.98 GiB 40006.52 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 162816 sectors
   Super Offset : 8 sectors
   Unused Space : before=162728 sectors, after=100016 sectors
          State : clean
    Device UUID : b1153191:2509a89f:518cafc7:1bb9776c


    Update Time : Sun Dec  2 10:08:57 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : a1c70113 - correct
         Events : 128204


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 2
   Array State : AAAAA.AA.A.. ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdb:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 569f899d:8bed5eee:2d47c23f:33b2b337
           Name : TandarLinux:0  (local to host TandarLinux)
  Creation Time : Thu Jun  2 21:06:49 2016
     Raid Level : raid6
   Raid Devices : 12


 Avail Dev Size : 7813867184 (3725.94 GiB 4000.70 GB)
     Array Size : 39068871680 (37258.98 GiB 40006.52 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 162816 sectors
   Super Offset : 8 sectors
   Unused Space : before=162728 sectors, after=100016 sectors
          State : clean
    Device UUID : cb32e8b6:32591bb5:38d9dbdd:488a0293


    Update Time : Sun Dec  2 10:08:57 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 19a87053 - correct
         Events : 128204


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 7
   Array State : AAAAA.AA.A.. ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdc:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 569f899d:8bed5eee:2d47c23f:33b2b337
           Name : TandarLinux:0  (local to host TandarLinux)
  Creation Time : Thu Jun  2 21:06:49 2016
     Raid Level : raid6
   Raid Devices : 12


 Avail Dev Size : 7813874352 (3725.95 GiB 4000.70 GB)
     Array Size : 39068871680 (37258.98 GiB 40006.52 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 162816 sectors
   Super Offset : 8 sectors
   Unused Space : before=162728 sectors, after=100016 sectors
          State : clean
    Device UUID : 0da3820f:87c2a17d:c1e430bc:60349025


    Update Time : Sun Dec  2 10:08:57 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : abac1b83 - correct
         Events : 128204


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 1
   Array State : AAAAA.AA.A.. ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdd:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 569f899d:8bed5eee:2d47c23f:33b2b337
           Name : TandarLinux:0  (local to host TandarLinux)
  Creation Time : Thu Jun  2 21:06:49 2016
     Raid Level : raid6
   Raid Devices : 12


 Avail Dev Size : 7813854896 (3725.94 GiB 4000.69 GB)
     Array Size : 39068871680 (37258.98 GiB 40006.52 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 162816 sectors
   Super Offset : 8 sectors
   Unused Space : before=162728 sectors, after=100016 sectors
          State : clean
    Device UUID : a30fd760:e6c52972:f38acb8c:9b44e46b


    Update Time : Sun Dec  2 10:08:57 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 876f5e9 - correct
         Events : 128204


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 3
   Array State : AAAAA.AA.A.. ('A' == active, '.' == missing, 'R' == replacing)
/dev/sde:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 569f899d:8bed5eee:2d47c23f:33b2b337
           Name : TandarLinux:0  (local to host TandarLinux)
  Creation Time : Thu Jun  2 21:06:49 2016
     Raid Level : raid6
   Raid Devices : 12


 Avail Dev Size : 7813857968 (3725.94 GiB 4000.70 GB)
     Array Size : 39068871680 (37258.98 GiB 40006.52 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 162816 sectors
   Super Offset : 8 sectors
   Unused Space : before=162728 sectors, after=100016 sectors
          State : clean
    Device UUID : fa6d7d5f:e68182ee:060c7cc2:3153c952


    Update Time : Sun Dec  2 10:08:57 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : a00babea - correct
         Events : 128204


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 4
   Array State : AAAAA.AA.A.. ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdf:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 569f899d:8bed5eee:2d47c23f:33b2b337
           Name : TandarLinux:0  (local to host TandarLinux)
  Creation Time : Thu Jun  2 21:06:49 2016
     Raid Level : raid6
   Raid Devices : 12


 Avail Dev Size : 7813874352 (3725.95 GiB 4000.70 GB)
     Array Size : 39068871680 (37258.98 GiB 40006.52 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 162816 sectors
   Super Offset : 8 sectors
   Unused Space : before=162728 sectors, after=100016 sectors
          State : clean
    Device UUID : 9369a458:fcac0e9e:6ac55531:34d33ce8


    Update Time : Sun Dec  2 10:08:57 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 4d0b4c02 - correct
         Events : 128204


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 0
   Array State : AAAAAAAA.A.. ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdg:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 569f899d:8bed5eee:2d47c23f:33b2b337
           Name : TandarLinux:0  (local to host TandarLinux)
  Creation Time : Thu Jun  2 21:06:49 2016
     Raid Level : raid6
   Raid Devices : 12


 Avail Dev Size : 7813867184 (3725.94 GiB 4000.70 GB)
     Array Size : 39068871680 (37258.98 GiB 40006.52 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 162816 sectors
   Super Offset : 8 sectors
   Unused Space : before=162728 sectors, after=100016 sectors
          State : clean
    Device UUID : 463a8eb9:fa3d19a2:cfec5a8e:a9fe94c9


    Update Time : Sun Dec  2 10:08:57 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : f05de48e - correct
         Events : 128204


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 6
   Array State : AAAAA.AA.A.. ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdh:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 569f899d:8bed5eee:2d47c23f:33b2b337
           Name : TandarLinux:0  (local to host TandarLinux)
  Creation Time : Thu Jun  2 21:06:49 2016
     Raid Level : raid6
   Raid Devices : 12


 Avail Dev Size : 7813874352 (3725.95 GiB 4000.70 GB)
     Array Size : 39068871680 (37258.98 GiB 40006.52 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 162816 sectors
   Super Offset : 8 sectors
   Unused Space : before=162728 sectors, after=100016 sectors
          State : clean
    Device UUID : d3e5fc8c:2953d28a:17d70065:36bce0c5


    Update Time : Sun Dec  2 10:08:57 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 7f776922 - correct
         Events : 128204


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 9
   Array State : AAAAA.AA.A.. ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdi:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 569f899d:8bed5eee:2d47c23f:33b2b337
           Name : TandarLinux:0  (local to host TandarLinux)
  Creation Time : Thu Jun  2 21:06:49 2016
     Raid Level : raid6
   Raid Devices : 12


 Avail Dev Size : 7813874352 (3725.95 GiB 4000.70 GB)
     Array Size : 39068871680 (37258.98 GiB 40006.52 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 162816 sectors
   Super Offset : 8 sectors
   Unused Space : before=162728 sectors, after=100016 sectors
          State : clean
    Device UUID : 862f59ea:27e5bf10:0a333d33:8554a99b


    Update Time : Sun Dec  2 10:08:50 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 6db391e - correct
         Events : 128204


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 5
   Array State : AAAAAAAAAAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdj:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 569f899d:8bed5eee:2d47c23f:33b2b337
           Name : TandarLinux:0  (local to host TandarLinux)
  Creation Time : Thu Jun  2 21:06:49 2016
     Raid Level : raid6
   Raid Devices : 12


 Avail Dev Size : 7813874352 (3725.95 GiB 4000.70 GB)
     Array Size : 39068871680 (37258.98 GiB 40006.52 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 162816 sectors
   Super Offset : 8 sectors
   Unused Space : before=162728 sectors, after=100016 sectors
          State : clean
    Device UUID : 42bd4de5:b1fb7c8f:3fd4d156:d8d5929b


    Update Time : Sun Dec  2 10:08:50 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : a40affea - correct
         Events : 128199


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 11
   Array State : AAAAAAAAAAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdk:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 569f899d:8bed5eee:2d47c23f:33b2b337
           Name : TandarLinux:0  (local to host TandarLinux)
  Creation Time : Thu Jun  2 21:06:49 2016
     Raid Level : raid6
   Raid Devices : 12


 Avail Dev Size : 7813874352 (3725.95 GiB 4000.70 GB)
     Array Size : 39068871680 (37258.98 GiB 40006.52 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 162816 sectors
   Super Offset : 8 sectors
   Unused Space : before=162728 sectors, after=100016 sectors
          State : clean
    Device UUID : 22b6f009:66612e8a:c9a5c06f:ff555ea9


    Update Time : Sun Dec  2 10:08:50 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : ea19b02e - correct
         Events : 128199


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 10
   Array State : AAAAAAAAAAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdl:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 569f899d:8bed5eee:2d47c23f:33b2b337
           Name : TandarLinux:0  (local to host TandarLinux)
  Creation Time : Thu Jun  2 21:06:49 2016
     Raid Level : raid6
   Raid Devices : 12


 Avail Dev Size : 7813874352 (3725.95 GiB 4000.70 GB)
     Array Size : 39068871680 (37258.98 GiB 40006.52 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 162816 sectors
   Super Offset : 8 sectors
   Unused Space : before=162728 sectors, after=100016 sectors
          State : clean
    Device UUID : 445eb34f:2eb4e91e:51bb479c:e8d30af6


    Update Time : Sun Dec  2 10:08:50 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 3dcb3e87 - correct
         Events : 128199


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 8
   Array State : AAAAAAAAAAAA ('A' == active, '.' == missing, 'R' == replacing)

```

Following along with your thread here: [https://ubuntuforums.org/showthread.php?t=2399971&page=2](https://ubuntuforums.org/showthread.php?t=2399971&page=2)

Looks like the next step is to check blkid?

```

ryan:/home$ sudo blkid
/dev/sdb: UUID="8f335956-4acd-518d-9c42-8748610f1eb8" UUID_SUB="124ca74e-f1fe-d998-464f-1fe642359853" LABEL="TandarLinux:0" TYPE="linux_raid_member"
/dev/sda: UUID="8f335956-4acd-518d-9c42-8748610f1eb8" UUID_SUB="0ca6a284-e958-6ab8-1493-c00fc00d74f2" LABEL="TandarLinux:0" TYPE="linux_raid_member"
/dev/sdc: UUID="8f335956-4acd-518d-9c42-8748610f1eb8" UUID_SUB="095e4b54-8715-6f40-e9f9-345b0d7120f3" LABEL="TandarLinux:0" TYPE="linux_raid_member"
/dev/sdd: UUID="8f335956-4acd-518d-9c42-8748610f1eb8" UUID_SUB="0b1cb873-6b7c-7631-4a5c-524ca739b8c7" LABEL="TandarLinux:0" TYPE="linux_raid_member"
/dev/sdf: UUID="8f335956-4acd-518d-9c42-8748610f1eb8" UUID_SUB="8cf85c62-4771-5fb0-d7c5-21d53d6ebe12" LABEL="TandarLinux:0" TYPE="linux_raid_member"
/dev/sde: UUID="8f335956-4acd-518d-9c42-8748610f1eb8" UUID_SUB="bec97efd-2e9b-2dee-3aca-803de5ce010d" LABEL="TandarLinux:0" TYPE="linux_raid_member"
/dev/sdh: UUID="8f335956-4acd-518d-9c42-8748610f1eb8" UUID_SUB="8294689a-d349-9649-d38e-231bfe3e001b" LABEL="TandarLinux:0" TYPE="linux_raid_member"
/dev/sdg: UUID="8f335956-4acd-518d-9c42-8748610f1eb8" UUID_SUB="db80d0e8-307e-06c7-bc9b-48495c13a71a" LABEL="TandarLinux:0" TYPE="linux_raid_member"
/dev/sdq1: UUID="e0c6e297-33b4-470a-81e7-0296f1f62369" TYPE="ext4" PARTUUID="ab7135f3-01"
/dev/sdq5: UUID="f7e76288-d73f-4fc4-b617-99b158c9b07c" TYPE="swap" PARTUUID="ab7135f3-05"
/dev/sdm: UUID="42714771-b4b7-b10f-2786-2673a9b38e0b" UUID_SUB="ab51f34b-7a89-59cd-22f5-3116730b1e52" LABEL="TandarLinux:3" TYPE="linux_raid_member"
/dev/sdn: UUID="42714771-b4b7-b10f-2786-2673a9b38e0b" UUID_SUB="3ad67c2f-db77-56e4-94db-968db1e19be9" LABEL="TandarLinux:3" TYPE="linux_raid_member"
/dev/sdp: UUID="42714771-b4b7-b10f-2786-2673a9b38e0b" UUID_SUB="4b474d4f-6dd5-07b7-aad7-c8ba1f4ceb0b" LABEL="TandarLinux:3" TYPE="linux_raid_member"
/dev/sdo: UUID="42714771-b4b7-b10f-2786-2673a9b38e0b" UUID_SUB="67a216ae-2f4f-d276-9a22-1a397a4331bb" LABEL="TandarLinux:3" TYPE="linux_raid_member"
/dev/sdi: UUID="8f335956-4acd-518d-9c42-8748610f1eb8" UUID_SUB="8219c910-fed3-8bbe-8591-6834cba15fcb" LABEL="TandarLinux:0" TYPE="linux_raid_member"
/dev/sdj: UUID="8f335956-4acd-518d-9c42-8748610f1eb8" UUID_SUB="135e7274-b509-79fa-e422-91f0eeed368a" LABEL="TandarLinux:0" TYPE="linux_raid_member"
/dev/sdk: UUID="8f335956-4acd-518d-9c42-8748610f1eb8" UUID_SUB="a11f8ea0-c1ca-5c73-410a-f654d9a65073" LABEL="TandarLinux:0" TYPE="linux_raid_member"
/dev/sdl: UUID="8f335956-4acd-518d-9c42-8748610f1eb8" UUID_SUB="5587c04b-b800-2df2-d4c0-fdcac083f61a" LABEL="TandarLinux:0" TYPE="linux_raid_member"
/dev/sdr: UUID="42714771-b4b7-b10f-2786-2673a9b38e0b" UUID_SUB="f0b4e6bb-120d-1966-15c7-01c725dfab6b" LABEL="TandarLinux:3" TYPE="linux_raid_member"
/dev/sds: UUID="d6eb9b78-1cfa-a21f-17fc-c6ac118871ec" UUID_SUB="a873f157-86c5-61a1-d1e2-281cc05525bc" LABEL="TandarLinux:2" TYPE="linux_raid_member"
/dev/sdt: UUID="42714771-b4b7-b10f-2786-2673a9b38e0b" UUID_SUB="8ca24f54-df01-95d7-6522-e06d154ad847" LABEL="TandarLinux:3" TYPE="linux_raid_member"
/dev/md3: UUID="a957dedc-9ca3-4a65-9b2c-7589c8e7cf3a" TYPE="ext4"
/dev/sdu: UUID="d6eb9b78-1cfa-a21f-17fc-c6ac118871ec" UUID_SUB="5309cb8d-9794-a4dc-b9e4-7fdd841e589f" LABEL="TandarLinux:2" TYPE="linux_raid_member"
/dev/md2: UUID="255fbcda-1802-4159-bf5e-7709c52d625d" TYPE="ext4"



```

---

### Post by darkod on 2018-12-02
First, suggestion for the future (but too late to change this now): Do not use the disk designator as mdadm raid member (like /dev/sda, /dev/sdb, etc). Always create one big partition on the disk and use that. Like /dev/sda1, /dev/sdb1, etc...

Do not worry about the name of the array. Whether it got called md127 or md0 is not important.

Is that --examine output from before or after running the --create --assume-clean?

---

### Post by t4nd4r on 2018-12-02
> **darkod said:**
> 

Is that --examine output from before or after running the --create --assume-clean?

It is BEFORE.

Do you need a new one?

---

### Post by darkod on 2018-12-02
Yes, it is important the chunk size to match. You didn't set the parameter in your new --create so you have ti check if it's 512K again.

---

### Post by t4nd4r on 2018-12-02
Chunks look like the same.

```

ryan@TandarLinux:/home$ sudo mdadm --examine /dev/sd[fdbkigeclajh]
/dev/sda:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 8f335956:4acd518d:9c428748:610f1eb8
           Name : TandarLinux:0  (local to host TandarLinux)
  Creation Time : Sun Dec  2 12:08:32 2018
     Raid Level : raid6
   Raid Devices : 12


 Avail Dev Size : 7813775024 (3725.90 GiB 4000.65 GB)
     Array Size : 39068871680 (37258.98 GiB 40006.52 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=688 sectors
          State : clean
    Device UUID : 0ca6a284:e9586ab8:1493c00f:c00d74f2


Internal Bitmap : 8 sectors from superblock
    Update Time : Sun Dec  2 12:08:32 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 30a22dd6 - correct
         Events : 0


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 2
   Array State : AAAAAAAAAAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdb:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 8f335956:4acd518d:9c428748:610f1eb8
           Name : TandarLinux:0  (local to host TandarLinux)
  Creation Time : Sun Dec  2 12:08:32 2018
     Raid Level : raid6
   Raid Devices : 12


 Avail Dev Size : 7813775024 (3725.90 GiB 4000.65 GB)
     Array Size : 39068871680 (37258.98 GiB 40006.52 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=688 sectors
          State : clean
    Device UUID : 124ca74e:f1fed998:464f1fe6:42359853


Internal Bitmap : 8 sectors from superblock
    Update Time : Sun Dec  2 12:08:32 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 12995d9d - correct
         Events : 0


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 7
   Array State : AAAAAAAAAAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdc:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 8f335956:4acd518d:9c428748:610f1eb8
           Name : TandarLinux:0  (local to host TandarLinux)
  Creation Time : Sun Dec  2 12:08:32 2018
     Raid Level : raid6
   Raid Devices : 12


 Avail Dev Size : 7813775024 (3725.90 GiB 4000.65 GB)
     Array Size : 39068871680 (37258.98 GiB 40006.52 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=688 sectors
          State : clean
    Device UUID : 095e4b54:87156f40:e9f9345b:0d7120f3


Internal Bitmap : 8 sectors from superblock
    Update Time : Sun Dec  2 12:08:32 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : d4706c91 - correct
         Events : 0


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 1
   Array State : AAAAAAAAAAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdd:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 8f335956:4acd518d:9c428748:610f1eb8
           Name : TandarLinux:0  (local to host TandarLinux)
  Creation Time : Sun Dec  2 12:08:32 2018
     Raid Level : raid6
   Raid Devices : 12


 Avail Dev Size : 7813775024 (3725.90 GiB 4000.65 GB)
     Array Size : 39068871680 (37258.98 GiB 40006.52 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=688 sectors
          State : clean
    Device UUID : 0b1cb873:6b7c7631:4a5c524c:a739b8c7


Internal Bitmap : 8 sectors from superblock
    Update Time : Sun Dec  2 12:08:32 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : aa99bc74 - correct
         Events : 0


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 3
   Array State : AAAAAAAAAAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sde:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 8f335956:4acd518d:9c428748:610f1eb8
           Name : TandarLinux:0  (local to host TandarLinux)
  Creation Time : Sun Dec  2 12:08:32 2018
     Raid Level : raid6
   Raid Devices : 12


 Avail Dev Size : 7813775024 (3725.90 GiB 4000.65 GB)
     Array Size : 39068871680 (37258.98 GiB 40006.52 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=688 sectors
          State : clean
    Device UUID : bec97efd:2e9b2dee:3aca803d:e5ce010d


Internal Bitmap : 8 sectors from superblock
    Update Time : Sun Dec  2 12:08:32 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 278f8c1a - correct
         Events : 0


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 4
   Array State : AAAAAAAAAAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdf:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 8f335956:4acd518d:9c428748:610f1eb8
           Name : TandarLinux:0  (local to host TandarLinux)
  Creation Time : Sun Dec  2 12:08:32 2018
     Raid Level : raid6
   Raid Devices : 12


 Avail Dev Size : 7813775024 (3725.90 GiB 4000.65 GB)
     Array Size : 39068871680 (37258.98 GiB 40006.52 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=688 sectors
          State : clean
    Device UUID : 8cf85c62:47715fb0:d7c521d5:3d6ebe12


Internal Bitmap : 8 sectors from superblock
    Update Time : Sun Dec  2 12:08:32 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : ebfd2bf1 - correct
         Events : 0


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 0
   Array State : AAAAAAAAAAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdg:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 8f335956:4acd518d:9c428748:610f1eb8
           Name : TandarLinux:0  (local to host TandarLinux)
  Creation Time : Sun Dec  2 12:08:32 2018
     Raid Level : raid6
   Raid Devices : 12


 Avail Dev Size : 7813775024 (3725.90 GiB 4000.65 GB)
     Array Size : 39068871680 (37258.98 GiB 40006.52 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=688 sectors
          State : clean
    Device UUID : db80d0e8:307e06c7:bc9b4849:5c13a71a


Internal Bitmap : 8 sectors from superblock
    Update Time : Sun Dec  2 12:08:32 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 5273c34 - correct
         Events : 0


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 6
   Array State : AAAAAAAAAAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdh:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 8f335956:4acd518d:9c428748:610f1eb8
           Name : TandarLinux:0  (local to host TandarLinux)
  Creation Time : Sun Dec  2 12:08:32 2018
     Raid Level : raid6
   Raid Devices : 12


 Avail Dev Size : 7813775024 (3725.90 GiB 4000.65 GB)
     Array Size : 39068871680 (37258.98 GiB 40006.52 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=688 sectors
          State : clean
    Device UUID : 8294689a:d3499649:d38e231b:fe3e001b


Internal Bitmap : 8 sectors from superblock
    Update Time : Sun Dec  2 12:08:32 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : b833a39 - correct
         Events : 0


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 9
   Array State : AAAAAAAAAAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdi:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 8f335956:4acd518d:9c428748:610f1eb8
           Name : TandarLinux:0  (local to host TandarLinux)
  Creation Time : Sun Dec  2 12:08:32 2018
     Raid Level : raid6
   Raid Devices : 12


 Avail Dev Size : 7813775024 (3725.90 GiB 4000.65 GB)
     Array Size : 39068871680 (37258.98 GiB 40006.52 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=688 sectors
          State : clean
    Device UUID : 8219c910:fed38bbe:85916834:cba15fcb


Internal Bitmap : 8 sectors from superblock
    Update Time : Sun Dec  2 12:08:32 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : c07daedf - correct
         Events : 0


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 5
   Array State : AAAAAAAAAAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdj:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 8f335956:4acd518d:9c428748:610f1eb8
           Name : TandarLinux:0  (local to host TandarLinux)
  Creation Time : Sun Dec  2 12:08:32 2018
     Raid Level : raid6
   Raid Devices : 12


 Avail Dev Size : 7813775024 (3725.90 GiB 4000.65 GB)
     Array Size : 39068871680 (37258.98 GiB 40006.52 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=688 sectors
          State : clean
    Device UUID : 135e7274:b50979fa:e42291f0:eeed368a


Internal Bitmap : 8 sectors from superblock
    Update Time : Sun Dec  2 12:08:32 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : db1406b0 - correct
         Events : 0


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 11
   Array State : AAAAAAAAAAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdk:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 8f335956:4acd518d:9c428748:610f1eb8
           Name : TandarLinux:0  (local to host TandarLinux)
  Creation Time : Sun Dec  2 12:08:32 2018
     Raid Level : raid6
   Raid Devices : 12


 Avail Dev Size : 7813775024 (3725.90 GiB 4000.65 GB)
     Array Size : 39068871680 (37258.98 GiB 40006.52 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=688 sectors
          State : clean
    Device UUID : a11f8ea0:c1ca5c73:410af654:d9a65073


Internal Bitmap : 8 sectors from superblock
    Update Time : Sun Dec  2 12:08:32 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : cd922990 - correct
         Events : 0


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 10
   Array State : AAAAAAAAAAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdl:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 8f335956:4acd518d:9c428748:610f1eb8
           Name : TandarLinux:0  (local to host TandarLinux)
  Creation Time : Sun Dec  2 12:08:32 2018
     Raid Level : raid6
   Raid Devices : 12


 Avail Dev Size : 7813775024 (3725.90 GiB 4000.65 GB)
     Array Size : 39068871680 (37258.98 GiB 40006.52 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=688 sectors
          State : clean
    Device UUID : 5587c04b:b8002df2:d4c0fdca:c083f61a


Internal Bitmap : 8 sectors from superblock
    Update Time : Sun Dec  2 12:08:32 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 15425ab4 - correct
         Events : 0


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 8
   Array State : AAAAAAAAAAAA ('A' == active, '.' == missing, 'R' == replacing)



```

---

### Post by darkod on 2018-12-02
Unfortunately, it looks like the array is correctly recreated on mdadm level.

But I don't see the filesystem detected in the blkid output. Did it have ext4 filesystem or something else?

It doesn't seem to detect any filesystem, which might be because of the failure. But I can't be sure.

Bottom line is, if the mdadm recreate has the correct device order, that is as much as you can do on mdadm level. If the filesystem is not detected you need to start working/researching filesystem recovery methods.

---

### Post by t4nd4r on 2018-12-02
It had an ext4 filesystem.

```

ryan@TandarLinux:/home$ sudo mke2fs -n /dev/sdc
mke2fs 1.42.13 (17-May-2015)
/dev/sdc contains a linux_raid_member file system labelled 'TandarLinux:0'
Proceed anyway? (y,n) y
Creating filesystem with 976754646 4k blocks and 244195328 inodes
Filesystem UUID: dee48e81-c3fe-4205-8c83-a9f7d50c25f8
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
        102400000, 214990848, 512000000, 550731776, 644972544

```

I started trying to restore from those superblock blocks, but I'm halfway through and getting no luck.

```



ryan@TandarLinux:/home$ sudo e2fsck -b 2654208 /dev/sdc
e2fsck 1.42.13 (17-May-2015)
e2fsck: Bad magic number in super-block while trying to open /dev/sdc


The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>


```

---

### Post by darkod on 2018-12-02
Why are you operating on /dev/sdc?

In mdadm array the filesystem is on the array itself, not the disks/partitions. The filesystem is on /dev/md127 (or /dev/md0, etc).

---

### Post by t4nd4r on 2018-12-02
I don't have any numbers after any of my drives for that array.


Guess I'm screwed?

---

### Post by darkod on 2018-12-02
I didn't understand the last post. What numbers after the drives do you expect?

---

### Post by darkod on 2018-12-02
Can you post which is the array name exactly please? The output of:
```
cat /proc/mdstat
```

---

### Post by t4nd4r on 2018-12-02
Sorry, after the drive for the md127 (used to be md0) I don't have an ext4 filesystem that I can see.

However, I keep being told there is existing [COLOR=#000000][FONT=&amp]linux_raid_member file system labelled 'TandarLinux:0'[/FONT][/COLOR]

```



ryan@TandarLinux:/home/e2/e2fsprogs/build$ sudo cat /proc/mdstat
Personalities : [raid1] [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid10]
md2 : active raid1 sds[0] sdu[1]
      2930135488 blocks super 1.2 [2/2] [UU]
      bitmap: 0/22 pages [0KB], 65536KB chunk


md127 : active (auto-read-only) raid6 sdd[1] sdf[0] sda[2] sdc[3] sde[4] sdg[6] sdb[7] sdh[9] sdk[10] sdi[5] sdl[8] sdj[11]
      39068871680 blocks super 1.2 level 6, 512k chunk, algorithm 2 [12/12] [UUUUUUUUUUUU]
      bitmap: 0/30 pages [0KB], 65536KB chunk


md3 : active raid6 sdt[4] sdr[5] sdp[3] sdo[2] sdm[0] sdn[1]
      31255580672 blocks super 1.2 level 6, 512k chunk, algorithm 2 [6/6] [UUUUUU]
      bitmap: 0/59 pages [0KB], 65536KB chunk


unused devices: <none>



```

I've also been trying to restore the superblock using 

```

ryan@TandarLinux:/home/e2/e2fsprogs/build$ sudo mke2fs -O 64bit,has_journal,extents,huge_file,flex_bg,uninit_bg,dir_nlink,extra_isize -n /dev/md127
mke2fs 1.44.4 (18-Aug-2018)
Creating filesystem with 9767217920 4k blocks and 610451456 inodes
Filesystem UUID: 474254b2-c1f7-494b-9a8e-9229a7e23519
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
        102400000, 214990848, 512000000, 550731776, 644972544, 1934917632,
        2560000000, 3855122432, 5804752896

```

None of those blocks seem to be working.

here's more detail info from mdadm
```

ryan@TandarLinux:/home/e2/e2fsprogs/build$ sudo mdadm --detail /dev/md127
/dev/md127:
        Version : 1.2
  Creation Time : Sun Dec  2 12:08:32 2018
     Raid Level : raid6
     Array Size : 39068871680 (37258.98 GiB 40006.52 GB)
  Used Dev Size : 3906887168 (3725.90 GiB 4000.65 GB)
   Raid Devices : 12
  Total Devices : 12
    Persistence : Superblock is persistent


  Intent Bitmap : Internal


    Update Time : Sun Dec  2 12:08:32 2018
          State : clean
 Active Devices : 12
Working Devices : 12
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : TandarLinux:0  (local to host TandarLinux)
           UUID : 8f335956:4acd518d:9c428748:610f1eb8
         Events : 0


    Number   Major   Minor   RaidDevice State
       0       8       80        0      active sync   /dev/sdf
       1       8       48        1      active sync   /dev/sdd
       2       8        0        2      active sync   /dev/sda
       3       8       32        3      active sync   /dev/sdc
       4       8       64        4      active sync   /dev/sde
       5       8      128        5      active sync   /dev/sdi
       6       8       96        6      active sync   /dev/sdg
       7       8       16        7      active sync   /dev/sdb
       8       8      176        8      active sync   /dev/sdl
       9       8      112        9      active sync   /dev/sdh
      10       8      160       10      active sync   /dev/sdk
      11       8      144       11      active sync   /dev/sdj


```

---

### Post by darkod on 2018-12-02
The TandarLinux:0 is not related to a filesystem in any way. It is simply the name of the array that was set.

Unfortunately it looks like there is no filesystem detected really. mdadm can't help you any more.

If you used the correct device order in the array and the correct chunk size, it should reassemble and show the filesystem (even if it is little corrupted).

This looks like nothing at all is detected...

---

### Post by t4nd4r on 2018-12-02
All right, no worries.

Can you verify I'm doing this correctly then to start over?

sudo mdadm --create --verbose /dev/md0 --level=6 --raid-devices=12 /dev/sda /dev/sdb /dev/sdc /dev/sdd /dev/sde /dev/sdf /dev/sdg /dev/sdh /dev/sdi /dev/sdj /dev/sdk /dev/sdl

Then I make a partition on it? 

[COLOR=#000000][FONT=Arial]sudo mkfs.ext4 /dev/md0


[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

### Post by darkod on 2018-12-02
To start over from scratch, deleting all data?

If that is what you want to do, yes. You can use that command to create new raid6 md0 array, and then with the second one to format it to ext4.

But if you are starting from zero, I would create one big partition on each of those disks, and use partitions in the mdadm array (/dev/sda1, /dev/sdb1, /dev/sdc1...).

---

### Post by t4nd4r on 2018-12-02
What's the reasoning for doing it like that?

I thought the RAID shares all 1 partition?

Here is what it looks like now

```



ryan@TandarLinux:/home/media$ sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL   NAME   FSTYPE              SIZE MOUNTPOINT   LABEL
sdf    linux_raid_member   3.7T              TandarLinux:0
&#9492;&#9472;md0  ext4               36.4T /media
sdo    linux_raid_member   7.3T              TandarLinux:3
&#9492;&#9472;md3  ext4               29.1T /home/media3
sdd    linux_raid_member   3.7T              TandarLinux:0
&#9492;&#9472;md0  ext4               36.4T /media
sdm    linux_raid_member   7.3T              TandarLinux:3
&#9492;&#9472;md3  ext4               29.1T /home/media3
sdu    linux_raid_member   2.7T              TandarLinux:2
&#9492;&#9472;md2  ext4                2.7T /home/media2
sdb    linux_raid_member   3.7T              TandarLinux:0
&#9492;&#9472;md0  ext4               36.4T /media
sdk    linux_raid_member   3.7T              TandarLinux:0
&#9492;&#9472;md0  ext4               36.4T /media
sds    linux_raid_member   2.7T              TandarLinux:2
&#9492;&#9472;md2  ext4                2.7T /home/media2
sdi    linux_raid_member   3.7T              TandarLinux:0
&#9492;&#9472;md0  ext4               36.4T /media
sdq                      465.8G
&#9500;&#9472;sdq2                       1K
&#9500;&#9472;sdq5 swap                7.9G [SWAP]
&#9492;&#9472;sdq1 ext4              457.9G /
sdg    linux_raid_member   3.7T              TandarLinux:0
&#9492;&#9472;md0  ext4               36.4T /media
sde    linux_raid_member   3.7T              TandarLinux:0
&#9492;&#9472;md0  ext4               36.4T /media
sdn    linux_raid_member   7.3T              TandarLinux:3
&#9492;&#9472;md3  ext4               29.1T /home/media3
sdc    linux_raid_member   3.7T              TandarLinux:0
&#9492;&#9472;md0  ext4               36.4T /media
sdl    linux_raid_member   3.7T              TandarLinux:0
&#9492;&#9472;md0  ext4               36.4T /media
sdt    linux_raid_member   7.3T              TandarLinux:3
&#9492;&#9472;md3  ext4               29.1T /home/media3
sda    linux_raid_member   3.7T              TandarLinux:0
&#9492;&#9472;md0  ext4               36.4T /media
sdj    linux_raid_member   3.7T              TandarLinux:0
&#9492;&#9472;md0  ext4               36.4T /media
sdr    linux_raid_member   7.3T              TandarLinux:3
&#9492;&#9472;md3  ext4               29.1T /home/media3
sdh    linux_raid_member   3.7T              TandarLinux:0
&#9492;&#9472;md0  ext4               36.4T /media
sdp    linux_raid_member   7.3T              TandarLinux:3
&#9492;&#9472;md3  ext4               29.1T /home/media3


```

If you care to walk me through the explanation/steps I would greatly appreciate it!

---

### Post by darkod on 2018-12-03
I don't think there is a really strong reason. It is mainly personal preference I think.

mdadm does not work like HW raid. You have the option to use partitions, as such I prefer to partition the HDD instead of using it "raw".

Also there is small possibility for disks from different models/manufacturers to have slightly different total number of sectors. By using a partition you can adjust identical partitions. You can't do that when using the disk as device because the total bytes are what they are.

I always leave 15-20MiB unpartitioned at the end of the disk, that way buying new disk in the future allows me to create the identical partition size even if the disk is 2-3MiB smaller.

If you buy 4TB disk tomorrow and it is only 2MiB smaller then the current ones (which is only 0.05% and can happen), the array will deny to add it. Because you can't add smaller member to already existing array. Only identical or bigger. But you don't control the total bytes on the HDD you buy. You can only control the bytes size of the partition you create yourself.

---

