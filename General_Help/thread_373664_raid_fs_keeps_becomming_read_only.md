---
title: "raid fs keeps becomming read only"
date: 2007-03-01
forum: General Help
---

### Post by sahendrickson on 2007-03-01
I've set up a software raided system. The root folder is mounted from /dev/md0, which is a raid 1 of /dev/sda1 & /dev/sdb1. It works fine, then eventually the root folder becomes read-only. It seems to do this after a while of inactivity. Any ideas what might be causing this -- or how I could find out?

Some (hopefully relevant) information is below...

Thanks,
-- Scott

--------------------------------------------------------------- fstab

:/#  cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md0
UUID=908f8901-5195-480f-baec-974c1e6e80d0 /               ext3    defaults        0       1
# /dev/sda3
UUID=910fd70a-a40d-46a7-a180-bcb962ce2896 /boot           ext3    defaults        0       2
# /dev/sda2
UUID=20468928-5be7-4b88-977f-b703b01b1561 none            swap    sw              0       0
# /dev/sdb2
UUID=57e6cfb3-f06e-42e5-8b73-b5323aebc5b3 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0

--------------------------------------------------------------- mdadm output

:/# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Wed Feb 28 09:45:01 2007
     Raid Level : raid1
     Array Size : 302744768 (288.72 GiB 310.01 GB)
    Device Size : 302744768 (288.72 GiB 310.01 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Mar  1 12:30:13 2007
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : bfcb259b:70acac3c:5afcbb59:f140967a
         Events : 0.4566

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
root@scottalton:/var/svn#

--------------------------------------------------------------- error output

:/# touch verifyall
touch: cannot touch `verifyall': Read-only file system

---

