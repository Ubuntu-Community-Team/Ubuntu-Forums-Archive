---
title: "mdadm raid 5 inactive smart failure help"
date: 2015-11-29
forum: General Help
---

### Post by 3gemail on 2015-11-29
I have a raid 5 setup with mdadm, the raid is showing inactive. It was originally created with 3 live drives and one hot spare.  The original server hardware failed as well so I moved it to new hardware.  The OS boots with no problem, but the raid will not come online.  I need help making the raid active again. 

cat /proc/mdstat only shows 3 drives in the raid. It had sdf1, but that is the failing drive.
```
 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md127 : inactive sde1[3](S) sdd1[1](S) sdc1[0](S)
      5860147414 blocks super 1.2


```

I tried to stop the raid and force reassemble, but received this error:

```
  mdadm --assemble --force /dev/md127 /dev/sd[cdef]
mdadm: Cannot assemble mbr metadata on /dev/sdc
mdadm: /dev/sdc has no superblock - assembly aborted
```

I get the same error for /dev/sdd if I remove sdc from the line.  

I ran  mdadm -E /dev/sdc1 and received the following:

```
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : fd04c4be:f6c41250:5ff3684d:d7943750
           Name : mythtv:0  (local to host mythtv)
  Creation Time : Thu Oct  2 08:52:26 2014
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3906764943 (1862.89 GiB 2000.26 GB)
     Array Size : 3906763776 (3725.78 GiB 4000.53 GB)
  Used Dev Size : 3906763776 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 7488d0e5:551aae85:19e8d1e7:c30a44c3

    Update Time : Sun Nov 22 09:49:16 2015
       Checksum : 80e41337 - correct
         Events : 161482

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : A.. ('A' == active, '.' == missing)
```

Thanks in advance for your help.

---

