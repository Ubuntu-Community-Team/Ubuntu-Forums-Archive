---
title: "RAID5 permissions issue"
date: 2007-04-06
forum: General Help
---

### Post by gurgle on 2007-04-06
I have successfully set up my RAID5 array using the ubuntu server edgy edition. I have this information from webmin:

**> mdadm --detail /dev/md0**
/dev/md0:
        Version : 00.90.03
  Creation Time : Thu Apr  5 21:25:53 2007
     Raid Level : raid5
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
    Device Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Apr  6 19:16:12 2007
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 8e8d4de0:44d756e2:9dfb1a28:fb817c77
         Events : 0.32

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1

I have the mount point set to:

 /mnt/raid 

but when I try and copy files or create folders in that folder I get a "permissions denied" error. Help would be appreciated!! :)

---

### Post by mgrusin on 2007-05-09
I just had to deal with the same thing.  If you haven't solved it yet, try this (sorry if this is too basic, not sure how much Unix you know):

From a terminal, type the command "[FONT="Courier New"]ls -ld /mnt/raid[/FONT]" (after you've mounted it).

It should report something like:

[FONT="Courier New"]drwxrwxr-x 8 root plugdev 4096 2007-05-07 07:46 /mnt/raid[/FONT]

The "drwxrwxr-x" are the permissions for the directory, "root" is the owner, and "plugdev" is the group.

When I created my raid, the owner and group were both "root", and since I'm not a member of the "root" group, I didn't have write access.  (Type "groups" to see what groups you belong to).

So I changed the group to "plugdev" by typing "[FONT="Courier New"]sudo chgrp plugdev /mnt/raid[/FONT]"

In order for this to work, the read/write/execute permissions should also be set for the group.  The group permissions are the middle "rwx" in the above "drwxrwxr-x".  (The first 3 are for the owner, the middle 3 are for the group, and the last 3 are for everyone else).  If the middle letters aren't "rwx", you can change them to "rwx" by typing "[FONT="Courier New"]sudo chmod g+rwx /mnt/raid[/FONT]"

I can think of other ways of doing this (adding yourself to the "root" group, changing the permissions for "everyone" to "rwx", changing the owner to yourself), if anyone thinks another way is better, let me know!

Here's another tip: it looks like if you mount your raid in /media instead of /mnt, it will show up on the desktop as a drive icon, which is kind of cool.

Good luck, hope this helps!  -MG.

---

