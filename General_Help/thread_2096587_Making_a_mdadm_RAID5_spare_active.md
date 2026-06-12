---
title: "Making a mdadm RAID5 spare active"
date: 2012-12-20
forum: General Help
---

### Post by bobbob1016 on 2012-12-20
I have a mdadm RAID5 with a drive that failed, and a spare that won't re-add as active.
How can I force it to be active, without losing data?

It is "clean" but degraded.  It mounted before with two missing, and one spare, but after a reboot, I can't do that anymore.  When I try -D it says doesn't appear to be active, even after an "mdadm --assemble --scan" (or manually listing drives).  I can do -D if I go to recovery mode from boot, and a root shell, but I can't mount the drive.

I'd appreciate any help:

sudo mdadm --examine /dev/sd[abcdef]1 
/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : c1811280:319e895b:fb456394:68582572
           Name : Ubuntu-Server:0
  Creation Time : Wed Jul 20 12:54:24 2011
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 2930269954 (1397.26 GiB 1500.30 GB)
     Array Size : 14651345920 (6986.31 GiB 7501.49 GB)
  Used Dev Size : 2930269184 (1397.26 GiB 1500.30 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 9319a9fb:cffc8626:42b760a3:f57e10ee

    Update Time : Thu Dec 20 08:20:32 2012
       Checksum : 61e1ea26 - correct
         Events : 994012

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AA.AA. ('A' == active, '.' == missing)
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : c1811280:319e895b:fb456394:68582572
           Name : Ubuntu-Server:0
  Creation Time : Wed Jul 20 12:54:24 2011
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 2930269954 (1397.26 GiB 1500.30 GB)
     Array Size : 14651345920 (6986.31 GiB 7501.49 GB)
  Used Dev Size : 2930269184 (1397.26 GiB 1500.30 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : f29f7e4d:fa6dde33:06012f0e:58a015a4

    Update Time : Thu Dec 20 08:20:32 2012
       Checksum : e1e24cd8 - correct
         Events : 994012

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : AA.AA. ('A' == active, '.' == missing)
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : c1811280:319e895b:fb456394:68582572
           Name : Ubuntu-Server:0
  Creation Time : Wed Jul 20 12:54:24 2011
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 2930272256 (1397.26 GiB 1500.30 GB)
     Array Size : 14651345920 (6986.31 GiB 7501.49 GB)
  Used Dev Size : 2930269184 (1397.26 GiB 1500.30 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 1cbf608f:c77b2544:32ff467f:1287c03f

    Update Time : Thu Dec 20 08:20:32 2012
       Checksum : 40ce7e32 - correct
         Events : 994012

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AA.AA. ('A' == active, '.' == missing)
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : c1811280:319e895b:fb456394:68582572
           Name : Ubuntu-Server:0
  Creation Time : Wed Jul 20 12:54:24 2011
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 2930272256 (1397.26 GiB 1500.30 GB)
     Array Size : 14651345920 (6986.31 GiB 7501.49 GB)
  Used Dev Size : 2930269184 (1397.26 GiB 1500.30 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : f9a18cbb:1605fc0b:861e0536:66cd970f

    Update Time : Thu Dec 20 08:20:32 2012
       Checksum : bb66398b - correct
         Events : 994012

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 4
   Array State : AA.AA. ('A' == active, '.' == missing)
/dev/sde1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : c1811280:319e895b:fb456394:68582572
           Name : Ubuntu-Server:0
  Creation Time : Wed Jul 20 12:54:24 2011
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 2930269954 (1397.26 GiB 1500.30 GB)
     Array Size : 14651345920 (6986.31 GiB 7501.49 GB)
  Used Dev Size : 2930269184 (1397.26 GiB 1500.30 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : f848a59a:9a42541a:e0bbcd90:151a0e52

    Update Time : Thu Dec 20 08:20:32 2012
       Checksum : 4615ff1b - correct
         Events : 994012

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : spare
   Array State : AA.AA. ('A' == active, '.' == missing)
/dev/sdf1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : c1811280:319e895b:fb456394:68582572
           Name : Ubuntu-Server:0
  Creation Time : Wed Jul 20 12:54:24 2011
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 2930269954 (1397.26 GiB 1500.30 GB)
     Array Size : 14651345920 (6986.31 GiB 7501.49 GB)
  Used Dev Size : 2930269184 (1397.26 GiB 1500.30 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : c0fd21c6:3793a1ff:ed133140:237e2953

    Update Time : Mon Dec 17 12:23:52 2012
       Checksum : 75785aa - correct
         Events : 895834

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 5
   Array State : AAAAAA ('A' == active, '.' == missing)

---

