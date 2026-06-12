---
title: "Problem with raid1 array after upgrade to 14.04"
date: 2014-05-30
forum: General Help
---

### Post by ejoftheweb on 2014-05-30
The upgrade to 14.04 broke my grub, so I used boot-repair-disk to fix matters.
Now, I'm in, but my /home is not mounted.

/home was on a 2-disk RAID1 array. It was formatted with ext4. 

Using mdadm -A it assembles fine, but it won't mount: "can't read superblock".

So I try running fsck, and then e2fsck -c and get

 ```
e2fsck: Invalid argument while trying to open /dev/md0

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem. 
```

Output of /proc/mdstat:
 
```
Personalities : 
md0 : inactive sdc1[0] sdd1[1]
      976507904 blocks super 1.2
       
unused devices: <none>
```

mdadm --examine gives the following, nothing seems untoward.

```

edward@Study:~/Desktop$ sudo mdadm --examine /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 79a52683:136ea3ef:48016435:ea363ed2
           Name : Study:0  (local to host Study)
  Creation Time : Tue Oct 30 18:00:09 2012
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 976506880 (465.63 GiB 499.97 GB)
     Array Size : 488253248 (465.63 GiB 499.97 GB)
  Used Dev Size : 976506496 (465.63 GiB 499.97 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : c1f4f2d5:ff2c0472:8c51c6b3:c4a6d5ad

    Update Time : Wed May 28 12:34:54 2014
       Checksum : 4a14e4dc - correct
         Events : 746


   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing)
edward@Study:~/Desktop$ sudo mdadm --examine /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 79a52683:136ea3ef:48016435:ea363ed2
           Name : Study:0  (local to host Study)
  Creation Time : Tue Oct 30 18:00:09 2012
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 976508928 (465.64 GiB 499.97 GB)
     Array Size : 488253248 (465.63 GiB 499.97 GB)
  Used Dev Size : 976506496 (465.63 GiB 499.97 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : b303615e:e954e336:c78db6e1:f02f056e

    Update Time : Wed May 28 12:34:54 2014
       Checksum : 8581e91d - correct
         Events : 746
 

   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing)
edward@Study:~/Desktop$ sudo mdadm --examine /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 79a52683:136ea3ef:48016435:ea363ed2
           Name : Study:0  (local to host Study)
  Creation Time : Tue Oct 30 18:00:09 2012
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 976506880 (465.63 GiB 499.97 GB)
     Array Size : 488253248 (465.63 GiB 499.97 GB)
  Used Dev Size : 976506496 (465.63 GiB 499.97 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : c1f4f2d5:ff2c0472:8c51c6b3:c4a6d5ad

    Update Time : Wed May 28 12:34:54 2014
       Checksum : 4a14e4dc - correct
         Events : 746


   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing)
edward@Study:~/Desktop$ sudo mdadm --examine /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 79a52683:136ea3ef:48016435:ea363ed2
           Name : Study:0  (local to host Study)
  Creation Time : Tue Oct 30 18:00:09 2012
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 976508928 (465.64 GiB 499.97 GB)
     Array Size : 488253248 (465.63 GiB 499.97 GB)
  Used Dev Size : 976506496 (465.63 GiB 499.97 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : b303615e:e954e336:c78db6e1:f02f056e

    Update Time : Wed May 28 12:34:54 2014
       Checksum : 8581e91d - correct
         Events : 746


   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing)
edward@Study:~/Desktop$ sudo mdadm --examine /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 79a52683:136ea3ef:48016435:ea363ed2
           Name : Study:0  (local to host Study)
  Creation Time : Tue Oct 30 18:00:09 2012
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 976506880 (465.63 GiB 499.97 GB)
     Array Size : 488253248 (465.63 GiB 499.97 GB)
  Used Dev Size : 976506496 (465.63 GiB 499.97 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : c1f4f2d5:ff2c0472:8c51c6b3:c4a6d5ad

    Update Time : Wed May 28 12:34:54 2014
       Checksum : 4a14e4dc - correct
         Events : 746


   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing)
edward@Study:~/Desktop$ sudo mdadm --examine /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 79a52683:136ea3ef:48016435:ea363ed2
           Name : Study:0  (local to host Study)
  Creation Time : Tue Oct 30 18:00:09 2012
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 976508928 (465.64 GiB 499.97 GB)
     Array Size : 488253248 (465.63 GiB 499.97 GB)
  Used Dev Size : 976506496 (465.63 GiB 499.97 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : b303615e:e954e336:c78db6e1:f02f056e

    Update Time : Wed May 28 12:34:54 2014
       Checksum : 8581e91d - correct
         Events : 746


   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing)

```

---

### Post by ejoftheweb on 2014-05-31
The output of /proc/mdstat shows no kernel raid support under the Personalities line. So it's a kernel problem. Right, back in the day when I used Gentoo I'd reconfigure the kernel to use the relevant modules. Now why haven't they been loaded now?

---

### Post by ejoftheweb on 2014-05-31
The output of /proc/mdstat shows no kernel raid support under the Personalities line. So mdadm thinks the array is active but the kernel thinks it's inactive because it, the kernel, hasn't loaded the right module(s), which might be CONFIG_MD and/or CONFIG_MD_RAID1?

---

