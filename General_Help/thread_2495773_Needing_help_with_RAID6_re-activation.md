---
title: "Needing help with RAID6 re-activation"
date: 2024-03-01
forum: General Help
---

### Post by mrkukov2 on 2024-03-01
Hi,


I have an RAID 6 array that is not having its 6 disks activated. Now after reading more instructions it's clear that using webmin to create RAID devices is a bad thing. You end up using the whole disk instead of partitions of them.


All 6 disks should be ok and data should be clean. The array broke after I moved the server to another location (sata cables might be in different order etc). The original reason for the changes was an USB drive that broke up... yep, there was the backups. #-o That broken disk was in fstab and therefore ubuntu went to recovery mode (since disk was not available). So backups are now kind of broken too.




Autodiscovery does find the array:
RAID level - RAID6 (Dual Distributed Parity)
Filesystem status - Inactive and not mounted


Here's report from mdadm examine:


sudo mdadm --examine /dev/sd[c,b,d,e,f,g]
/dev/sdc:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 2bf6381b:fe19bdd4:9cc53ae7:5dce1630
           Name : NAS-ubuntu:0
  Creation Time : Thu May 18 22:56:47 2017
     Raid Level : raid6
   Raid Devices : 6


 Avail Dev Size : 7813782192 sectors (3.64 TiB 4.00 TB)
     Array Size : 15627548672 KiB (14.55 TiB 16.00 TB)
  Used Dev Size : 7813774336 sectors (3.64 TiB 4.00 TB)
    Data Offset : 254976 sectors
   Super Offset : 8 sectors
   Unused Space : before=254896 sectors, after=7856 sectors
          State : clean
    Device UUID : b944e546:6c1c3cf9:b3c6294a:effa679a


Internal Bitmap : 8 sectors from superblock
    Update Time : Wed Feb 28 19:10:03 2024
  Bad Block Log : 512 entries available at offset 24 sectors
       Checksum : 4a9db132 - correct
         Events : 477468


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 5
   Array State : AAAAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdb:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
/dev/sdd:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
/dev/sde:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
/dev/sdf:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
/dev/sdg:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)






Since the disks have been used instead of partitions I'm now getting an error when trying to assemble:


$ sudo mdadm --assemble /dev/md0 /dev/sdc /dev/sdb /dev/sdd /dev/sde /dev/sdf /dev/sdg
mdadm: No super block found on /dev/sdb (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sdb
mdadm: /dev/sdb has no superblock - assembly aborted




$ sudo mdadm --assemble --force /dev/md0 /dev/sdb /dev/sdc /dev/sdd /dev/sde /dev/sdf /dev/sdg
mdadm: Cannot assemble mbr metadata on /dev/sdb
mdadm: /dev/sdb has no superblock - assembly aborted




Should I try to re-create that array again or how can I activate it properly? It seems that only 1 disk reports the array information correctly.


ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sdb  /dev/sdc  /dev/sdd  /dev/sde  /dev/sdf  /dev/sdg  /dev/sdh  /dev/sdh1


All disks should be fine. I have setup a warning if any device fails in the array and there has been no warnings. Also SMART data shows ok for all disks.








Basic info:


$uname -a
Linux NAS-server 5.15.0-97-generic #107-Ubuntu SMP Wed Feb 7 13:26:48 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux


$mdadm --version
mdadm - v4.2 - 2021-12-30


$ sudo mdadm --detail /dev/md0
/dev/md0:
           Version : 1.2
        Raid Level : raid6
     Total Devices : 1
       Persistence : Superblock is persistent


             State : inactive
   Working Devices : 1


              Name : NAS-ubuntu:0
              UUID : 2bf6381b:fe19bdd4:9cc53ae7:5dce1630
            Events : 477468


    Number   Major   Minor   RaidDevice


       -       8       32        -        /dev/sdc








So what should I do next?
I have not ran the --create --assume-clean yet but could that help in this case? 


Thanks for the help.

---

