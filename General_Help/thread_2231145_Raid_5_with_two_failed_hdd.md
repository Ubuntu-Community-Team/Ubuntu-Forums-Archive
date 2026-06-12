---
title: "Raid 5 with two failed hdd"
date: 2014-06-23
forum: General Help
---

### Post by lukas9 on 2014-06-23
Hi,

Died two disks in raid 5. The first few days ago, second today :/. 

Today, after the failure of the second disk array does not start. 
After the reboot second disk status is ok, smart without errors... 

Please suggestions how to resolve this problem. 

[B]/proc/mdstat:
[/B]
**md2 ??? - lost**

Personalities : [raid1] [linear] [raid0] [raid10] [raid6] [raid5] [raid4]
md1 : active raid1 sdb2[1] sde2[4] sda2[0] sdc2[2]
      2097088 blocks [12/4] [UUU_U_______]

md0 : active raid1 sdb1[1] sde1[4] sda1[0] sdc1[2]
      2490176 blocks [12/4] [UUU_U_______]

unused devices: <none>


**mdadm - examine:** 

An example of one of the disks:

/dev/sda3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 5d45f465:953b604e:b1060c33:b11a3d57
           Name : FS:2
  Creation Time : Fri Nov  9 16:27:56 2012
     Raid Level : raid5
   Raid Devices : 5

 Avail Dev Size : 5851088833 (2790.02 GiB 2995.76 GB)
     Array Size : 23404354048 (11160.07 GiB 11983.03 GB)
  Used Dev Size : 5851088512 (2790.02 GiB 2995.76 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : d0b7a87d:e9210253:d760f60e:36fe10c2

    Update Time : Mon Jun 23 20:03:38 2014
       Checksum : 19a4f866 - correct
         Events : 2610613

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 0
   Array State : A.A.A ('A' == active, '.' == missing)

---

