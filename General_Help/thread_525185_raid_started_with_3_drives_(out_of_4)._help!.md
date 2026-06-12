---
title: "raid started with 3 drives (out of 4). help!"
date: 2007-08-14
forum: General Help
---

### Post by nigelicious on 2007-08-14
I created a raid array with mdadm this Saturday using this guide - [http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188).

I have 4x320Gig brand new SATA drives.

I restarted the machine this morning and the raid was not present. I restarted the raid using :
```
sudo mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1
```
and got:
```
mdadm: /dev/md0 has been started with 3 drives (out of 4).
```

The output of sudo mdadm --query --detail /dev/md0 :
```
/dev/md0:
        Version : 00.90.03
  Creation Time : Sat Aug 11 18:31:05 2007
     Raid Level : raid5
     Array Size : 937705728 (894.27 GiB 960.21 GB)
    Device Size : 312568576 (298.09 GiB 320.07 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Aug 14 15:56:36 2007
          State : clean, degraded
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 7f4b4a1f:351d4de2:2638e78d:899a8498
         Events : 0.37258

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       0        0        3      removed

```

Can anyone advise me on why one of the drives may be listed as removed? There have been no physical changes to the server.

---

### Post by nigelicious on 2007-08-14
I have looked at the drives using gparted and they all seem to be present.
I've readded using sudo mdadm /dev/md0 -a /dev/sdd1 , but if anyone could enlighten me as to why it might not be added when i ran the first reassemble command, I'd really appreciate the assistance :)

---

### Post by fjgaude on 2007-08-14
I can't say why the fourth drive was dropped from the array, but you can add it back using mdadm. Then the array will rebuild with the forth drive there. It seems that at one time that drive was there. Once you have created the array I don't think you need to ever "assemble" it again. Try:

```

sudo mdadm /dev/md0 --re-add /dev/sdd1 
```

Carefully read the man pages for mdadm to understand what it all means.

Good luck, but be careful.

frank

---

