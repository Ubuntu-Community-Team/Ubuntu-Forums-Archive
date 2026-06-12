---
title: "ZFS Pool Hot Spare Issue"
date: 2022-02-25
forum: General Help
---

### Post by mallinss on 2022-02-25
Hello All, 
I noticed today with my Ubuntu Server that the hots spare assigned to my ZFS pool has a status of UNAVAIL, not sure what to do with this, as the actual disk number (sdd) is no longer reflective of what it was and now has this long number (0e21684c-dee4-11ea-8384-ac1f6bdd1381) associated. See output below, any ideas ?

Regards Steve

  pool: Data_Pool_One
 state: ONLINE
  scan: scrub repaired 0B in 0 days 11:45:07 with 0 errors on Sun Feb 13 12:09:08 2022
config:


        NAME                                    STATE     READ WRITE CKSUM
        Data_Pool_One                           ONLINE       0     0     0
          raidz1-0                              ONLINE       0     0     0
            sdh2                                ONLINE       0     0     0
            sdf2                                ONLINE       0     0     0
            sdc2                                ONLINE       0     0     0
            sdg2                                ONLINE       0     0     0
            sde2                                ONLINE       0     0     0
        logs
          sda1                                  ONLINE       0     0     0
        cache
          sdb1                                  ONLINE       0     0     0
        spares
          0e21684c-dee4-11ea-8384-ac1f6bdd1381  UNAVAIL 


errors: No known data errors

NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0         7:0    0  55.5M  1 loop /snap/core18/2253
loop1         7:1    0  61.9M  1 loop /snap/core20/1361
loop2         7:2    0  55.5M  1 loop /snap/core18/2284
loop3         7:3    0  67.2M  1 loop /snap/lxd/21835
loop4         7:4    0  67.9M  1 loop /snap/lxd/22526
loop5         7:5    0  43.6M  1 loop /snap/snapd/14978
loop6         7:6    0  61.9M  1 loop /snap/core20/1328
sda           8:0    0 465.8G  0 disk 
&#9500;&#9472;sda1        8:1    0 465.8G  0 part 
&#9492;&#9472;sda9        8:9    0     8M  0 part 
sdb           8:16   0 465.8G  0 disk 
&#9500;&#9472;sdb1        8:17   0 465.8G  0 part 
&#9492;&#9472;sdb9        8:25   0     8M  0 part 
sdc           8:32   0   5.5T  0 disk 
&#9500;&#9472;sdc1        8:33   0     2G  0 part 
&#9492;&#9472;sdc2        8:34   0   5.5T  0 part 
sdd           8:48   0   5.5T  0 disk 
&#9500;&#9472;sdd1        8:49   0     2G  0 part 
&#9492;&#9472;sdd2        8:50   0   5.5T  0 part 
sde           8:64   0   5.5T  0 disk 
&#9500;&#9472;sde1        8:65   0     2G  0 part 
&#9492;&#9472;sde2        8:66   0   5.5T  0 part 
sdf           8:80   0   5.5T  0 disk 
&#9500;&#9472;sdf1        8:81   0     2G  0 part 
&#9492;&#9472;sdf2        8:82   0   5.5T  0 part 
sdg           8:96   0   5.5T  0 disk 
&#9500;&#9472;sdg1        8:97   0     2G  0 part 
&#9492;&#9472;sdg2        8:98   0   5.5T  0 part 
sdh           8:112  0   5.5T  0 disk 
&#9500;&#9472;sdh1        8:113  0     2G  0 part 
&#9492;&#9472;sdh2        8:114  0   5.5T  0 part 
nvme0n1     259:0    0 232.9G  0 disk 
&#9500;&#9472;nvme0n1p1 259:1    0   512M  0 part /boot/efi
&#9492;&#9472;nvme0n1p2 259:2    0 232.4G  0 part /

---

### Post by #&amp;thj^% on 2022-02-25
1st get the zfs pool into UUID mode by zpool export pool and then zpool import -d /dev/disk/by-uuid pool

This then will allow you to detach the UNAVAIL drive, which "I" then wiped clean.
(your choice on this)
just rerun the process you used to re-identify the disks the first time:

 ```
   zpool export pool
    zpool import -d /dev/disk/by-id pool
```

This will unify the drives to the by-id format. You could use by-uuid instead if you prefer to have it be in that format.

---

### Post by mallinss on 2022-02-25
> **1fallen said:**
> 1st get the zfs pool into UUID mode by zpool export pool and then zpool import -d /dev/disk/by-uuid pool

This then will allow you to detach the UNAVAIL drive, which "I" then wiped clean.
(your choice on this)
just rerun the process you used to re-identify the disks the first time:

 ```
   zpool export pool
    zpool import -d /dev/disk/by-id pool
```

This will unify the drives to the by-id format. You could use by-uuid instead if you prefer to have it be in that format.


OK, thanks for the info, seems like once I did this, the drive came back to 'AVAIL' ... a bit odd.

  pool: Data_Pool_One
 state: ONLINE
  scan: scrub repaired 0B in 0 days 11:45:07 with 0 errors on Sun Feb 13 12:09:08 2022
config:


        NAME                                         STATE     READ WRITE CKSUM
        Data_Pool_One                                ONLINE       0     0     0
          raidz1-0                                   ONLINE       0     0     0
            wwn-0x5000c500c5fbeeb5-part2             ONLINE       0     0     0
            wwn-0x5000c500c5a6d285-part2             ONLINE       0     0     0
            wwn-0x5000c500c5fca44b-part2             ONLINE       0     0     0
            wwn-0x5000c500c5fc9fc4-part2             ONLINE       0     0     0
            wwn-0x5000c500c5a72751-part2             ONLINE       0     0     0
        logs
          wwn-0x5002538e3036211b-part1               ONLINE       0     0     0
        cache
          wwn-0x5002538e303628fc-part1               ONLINE       0     0     0
        spares
          scsi-SATA_ST6000VN001-2BB1_ZCT2H4N1-part2  AVAIL   


errors: No known data errors

---

### Post by #&amp;thj^% on 2022-02-25
Sometimes it just goes wacky, I never could figure the cause myself so resorted to reordering.
Regards

---

### Post by mallinss on 2022-02-25
Cheers for that :)

---

