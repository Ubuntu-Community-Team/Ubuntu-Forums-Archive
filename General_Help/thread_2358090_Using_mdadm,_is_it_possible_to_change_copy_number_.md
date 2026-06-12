---
title: "Using mdadm, is it possible to change copy number in Raid10 array?"
date: 2017-04-09
forum: General Help
---

### Post by zubbs1 on 2017-04-09
I am attempting to finally setup a raid10 array for my media collection to use on a dedicated server box.  I had no experience using mdadm, but followed [this tutorial]("https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04"), which was thorough and very helpful.  However, I failed to look closely at what I was doing, and failed to modify their code properly for my own purposes.  Specifically I entered this:
```

[LIST]
[*]sudo mdadm --create --verbose /dev/md0 --level=10 --layout=n3 --raid-devices=6 /dev/[COLOR=#E94849]sda[/COLOR] /dev/[COLOR=#E94849]sdb[/COLOR] /dev/[COLOR=#E94849]sdc[/COLOR] /dev/[COLOR=#E94849]sdd [/COLOR]/dev[COLOR=#E94849]/[COLOR=#E94849]sdf [/COLOR][/COLOR]/dev/[COLOR=#E94849][COLOR=#E94849]sdg[/COLOR] [/COLOR]
[/LIST]

```

my intention would have been to enter it this way:
```

[LIST]
[*]sudo mdadm --create --verbose /dev/md0 --level=10 [SIZE=3][COLOR=#ff0000]**--layout=n2**[/COLOR] [/SIZE]--raid-devices=6 /dev/[COLOR=#E94849]sda[/COLOR] /dev/[COLOR=#E94849]sdb[/COLOR] /dev/[COLOR=#E94849]sdc[/COLOR] /dev/[COLOR=#E94849]sdd [/COLOR]/dev[COLOR=#E94849]/[COLOR=#E94849]sdf [/COLOR][/COLOR]/dev/[COLOR=#E94849][COLOR=#E94849]sdg[/COLOR] [/COLOR]&#8203;
[/LIST]

```[COLOR=#E94849]
[/COLOR]```

~$ sudo mdadm -D /dev/md0:


        Version : 1.2
  Creation Time : Sun Apr  2 14:03:20 2017
     Raid Level : raid10
     Array Size : 11720661504 (11177.69 GiB 12001.96 GB)
  Used Dev Size : 3906887168 (3725.90 GiB 4000.65 GB)
   Raid Devices : 6
  Total Devices : 6
    Persistence : Superblock is persistent


  Intent Bitmap : Internal


    Update Time : Sun Apr  9 10:40:43 2017
          State : clean, degraded, recovering 
 Active Devices : 5
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 1


         Layout : near=2
     Chunk Size : 512K


 Rebuild Status : 2% complete


           Name : Marx:0  (local to host Marx)
           UUID : 412e2c9d:c4239440:5fa7a2b5:69b9353a
         Events : 32540


    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync set-A   /dev/sda
       1       8       16        1      active sync set-B   /dev/sdb
       2       8       32        2      active sync set-A   /dev/sdc
       6       8       80        3      active sync set-B   /dev/sdf
       7       8       96        4      spare rebuilding   /dev/sdg
       5       8       48        5      active sync set-B   /dev/sdd

```

```

~$ df -h -x devtmpfs -x tmpfs
Filesystem      Size  Used Avail Use% Mounted on
/dev/sde2       102G  6.6G   91G   7% /
/dev/sde1       511M  3.6M  508M   1% /boot/efi
/dev/md0        7.3T  6.6T  343G  96% /media/sharemore

```
Clearly I have three sets of two mirrors and only 7.3T available instead of rougly 12T as intended.

Quick aside: /dev/sdg had some sort of small partition that I did not see when I formed the array.  After a reboot, it was dropped form the /md0 array.  My pseudo-educated guess is that there was some interference on that partition that was not allowing the Superblock on that hard disk to be read/seen. I was able to use the disks utility to delete all partitions on /sdg.  I then had to force the reassembly without the /sdg disk which successfully rebuilt the array (with 5/6 disks present) I then was able to add the /sdg back into the /md0 array, causing the rebuilding (to fill in the third copy of 'A').


Really sorry for the long winded setup.  Here is my question:
Once this rebuild is complete and if it shows all six devices as active-sync, is there a means to change the layout to be --layout=n2 without losing the data?


Appreciate any help you can provide.

Cheers.

---

