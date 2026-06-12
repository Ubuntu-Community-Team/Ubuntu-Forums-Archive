---
title: "Raid 5 mdadm won't assemble"
date: 2008-04-14
forum: General Help
---

### Post by dinomight on 2008-04-14
Ok so i have a raid 5 setup on my box and after i rebooted the box last night the raid array didn't remount as it usually does.
I've tried running the array but it errors out saying that there is only one drive and that isn't enough. I need help, I don't know how to add the other two drives back into the array so that it will run properly. Below i have listed the mdm --examine for each of the drives an although the first drive show two drives disabled and the second drive shows 1 (third drive thinks everything is ok) I think each of the drives are really ok (i haven't written to the drives in a while so nothing should be out of sync. I'm afraid of doing a build or a create because i don't want to lose the data on the drives. If someone could show me how i can add all three drives from an existing array into the raid set so that it will mount i would really appreciate it . And if you need any more information on the drives or need me to run something just let me know and i'll send you the info.
```

mdadm --examine /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : ddf5dbf5:499deb25:19ffd938:6715fbff (local to host darknas)
  Creation Time : Fri Jun  1 23:34:11 2007
     Raid Level : raid5
    Device Size : 390708736 (372.61 GiB 400.09 GB)
     Array Size : 781417472 (745.22 GiB 800.17 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 0

    Update Time : Sun Apr 13 21:11:46 2008
          State : clean
 Active Devices : 1
Working Devices : 1
 Failed Devices : 2
  Spare Devices : 0
       Checksum : f78490fd - correct
         Events : 0.36116

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       0        0        1      faulty removed
   2     2       0        0        2      faulty removed



mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : ddf5dbf5:499deb25:19ffd938:6715fbff (local to host darknas)
  Creation Time : Fri Jun  1 23:34:11 2007
     Raid Level : raid5
    Device Size : 390708736 (372.61 GiB 400.09 GB)
     Array Size : 781417472 (745.22 GiB 800.17 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 0

    Update Time : Thu Apr 10 11:13:26 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : f7801042 - correct
         Events : 0.36112

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed


mdadm --examine /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : ddf5dbf5:499deb25:19ffd938:6715fbff (local to host darknas)
  Creation Time : Fri Jun  1 23:34:11 2007
     Raid Level : raid5
    Device Size : 390708736 (372.61 GiB 400.09 GB)
     Array Size : 781417472 (745.22 GiB 800.17 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Thu Mar  6 21:37:26 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : f75172b0 - correct
         Events : 0.66

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       33        2      active sync   /dev/sdc1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1


mdadm --assemble /dev/md0
mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.

```

---

### Post by tamoneya on 2008-04-14
what happens when you try ```
mdadm --assemble --scan
```That always seems to work for me.

---

### Post by dinomight on 2008-04-14
Ok so i made some progress with good and bad results.
I was able to 

mdadm --assemble --force /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1

and the raid set started again (albiet using only sda1 and sdb1) so i mounted the drive and started looking around but i ran into io errors everywhere so i unmounted and stopped the array and when i tried again it sais sdb1 was missing the superblock, so i tried it without sdb1 and just sda1 and sdc1 and that worked so this time i ran xfs_repair -L /dev/md0, and after much repair the drive was once again mountable, but this time things are scattered inside the lost+found directory which is ok i'm fine with that. It is just a file server and most of the directory tree is still intact. I lost some data but at least most of it is there. Now my problem is adding /dev/sdb1 back into the array, and having the raid5 rebuild that drive. If i try 
mdmadm -a /dev/md0 /dev/sdb1
i get the following error.
mdadm: add new device failed for /dev/sdb1 as 3: Invalid argument

Does anyone know how to add back sdb1 and have the raid 5 array start rebuilding. (i'm fairly certain that the drive is still ok.
And by the way now if i run 
mdadm --assemble --scan
it returns nothing.

---

