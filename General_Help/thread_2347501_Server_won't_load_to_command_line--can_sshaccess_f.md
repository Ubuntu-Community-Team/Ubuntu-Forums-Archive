---
title: "Server won't load to command line--can ssh/access fine"
date: 2016-12-26
forum: General Help
---

### Post by jeremy21 on 2016-12-26
Hello,
  got kind of an interesting problem I can't google-fu out of.  Running a little home server.  Trying to get to the command line after a boot-up to verify everything works before I reload it all and I get - 

```
/dev/sde1: clean, 107853/6815744 files, 1168411/27240960 blocks
```

  I can SSH to the server, login, do stuff, no problem.  Local workstations can access the server shares without issue.  Just can't ctrl^C/X/Z out of the above line on the monitor.

  Already tried restarting, didn't notice anything during start up.

  Here's some pertinent info, please let me know if there's something else that could help ID problem :

df
```

Filesystem      1K-blocks      Used  Available Use% Mounted on
udev              3971440         0    3971440   0% /dev
tmpfs              804612      9280     795332   2% /run
/dev/sde1       107121696   2831708   98825412   3% /
tmpfs             4023048         0    4023048   0% /dev/shm
tmpfs                5120         0       5120   0% /run/lock
tmpfs             4023048         0    4023048   0% /sys/fs/cgroup
/dev/md0       5813842984 710062944 4810756376  13% /srv
cgmfs                 100         0        100   0% /run/cgmanager/fs
tmpfs              804612         0     804612   0% /run/user/1000
```

fstab
```
fstab# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdf1 during installation
UUID=993f97d4-4482-4e8c-9136-bb49c519800a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdf5 during installation
UUID=917e0515-6b22-4c09-ae67-b99622268b50 none            swap    sw              0       0


#RAID 5 array on main sata controller
/dev/md0         /srv            ext4     defaults       1         2
```

 sudo mdadm -Q --detail /dev/md0
```
/dev/md0:        Version : 1.2
  Creation Time : Sat Mar 22 00:25:58 2014
     Raid Level : raid5
     Array Size : 5860145664 (5588.67 GiB 6000.79 GB)
  Used Dev Size : 1953381888 (1862.89 GiB 2000.26 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent


    Update Time : Mon Dec 26 00:04:29 2016
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : Server:0
           UUID : eefdf9d1:10e0bcb6:f7a5f726:4deb195d
         Events : 16192


    Number   Major   Minor   RaidDevice State
       0       8        5        0      active sync   /dev/sda5
       1       8       21        1      active sync   /dev/sdb5
       2       8       37        2      active sync   /dev/sdc5
       4       8       48        3      active sync   /dev/sdd
```

Thanks,

---

### Post by steeldriver on 2016-12-26
Have you tried switching to any of the other virtual terminals (Ctrl-Alt-F2 and so on)? does a login prompt show on any of those?

---

### Post by jeremy21 on 2016-12-26
And, yep I get a console prompt and can login.

Something I should be worried about?

---

### Post by SeijiSensei on 2016-12-26
Probably the server did not shut down cleanly the last time.  When that happens the boot manager runs fsck against any unclean partitions before continuing on.  That left the line you quoted in the original terminal, but there's nothing to worry about.  Did you try hitting return in that console?  Or Ctrl-C?

Try rebooting with "sudo reboot" from the command prompt and see what happens.  All the filesystems should be unmounted and not require an fsck at the next boot.

---

### Post by jeremy21 on 2016-12-26
Yep,

  Tired all the normal exit commands.  Nothing worked.  I'll try an orderly reboot now.

---

