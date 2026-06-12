---
title: "mdadm issues"
date: 2016-08-23
forum: General Help
---

### Post by Vaclav Vasek on 2016-08-23
I cannot save .odt file - getting error thet file doe not exist 
I can save *.ino file getting no errors but no cnfirmation either. t cannot open it from device , it is not there 
I have build md0 and according to mdadm it is running , but after reboot GParted shows md127 
The md127 device / partition is "unallocated"  in GParted.

Here is what mdadm outputs

Where did md0 went?

im@jim-desktop:~$ sudo mdadm --detail /dev/md0
mdadm: cannot open /dev/md0: No such file or directory
jim@jim-desktop:~$ sudo mdadm --detail /dev/md127
/dev/md127:
        Version : 1.2
     Raid Level : raid0
  Total Devices : 1
    Persistence : Superblock is persistent

          State : inactive

           Name : jim-desktop:0  (local to host jim-desktop)
           UUID : 32973ece:b35d9378:ad15d2be:91434228
         Events : 113

    Number   Major   Minor   RaidDevice

       -       8       18        -        /dev/sdb2

---

