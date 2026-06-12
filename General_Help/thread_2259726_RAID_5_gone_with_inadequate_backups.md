---
title: "RAID 5 gone with inadequate backups"
date: 2015-01-06
forum: General Help
---

### Post by tony66 on 2015-01-06
Guys - i need help.  I have a THECUS NAS which failed this past weekend.  4 x 1.5 TB drives installed.  i knew one was faulty and was going to replace it soon.  Nevertheless, i powered it off to move to a different location.  Powered it back up RAID=NONE.

I know it uses MDADM for RAID so i installed to my workstation and powered on with ubuntu.  All 4 drives detected which is good sign.  then i ran:

[FONT=arial]mdadm --examine --scan[/FONT]
[FONT=arial]ARRAY /dev/md/0 metadata=1.0 UUID=91a811aa:7e0d6edf:[/FONT][FONT=arial]cd06fd68:b82be96c name=ALPHA:0[/FONT]
[FONT=arial]ARRAY /dev/md1 UUID=5ff12998:9c1883a2:[/FONT][FONT=arial]37651b0a:3bbd305e

Alpha is the name of my array

Followed by:
[/FONT][FONT=arial]mdadm --assemble --scan --verbose[/FONT]
[FONT=arial]mdadm: looking for devices for /dev/md/0[/FONT]
[FONT=arial]mdadm: no RAID superblock on /dev/sde1[/FONT]
[FONT=arial]mdadm: no RAID superblock on /dev/sde[/FONT]
[FONT=arial]mdadm: no RAID superblock on /dev/sdd2[/FONT]
[FONT=arial]mdadm: /dev/sdd1 is busy - skipping[/FONT]
[FONT=arial]mdadm: no RAID superblock on /dev/sdd[/FONT]
[FONT=arial]mdadm: no RAID superblock on /dev/sdc2[/FONT]
[FONT=arial]mdadm: /dev/sdc1 is busy - skipping[/FONT]
[FONT=arial]mdadm: no RAID superblock on /dev/sdc[/FONT]
[FONT=arial]mdadm: no RAID superblock on /dev/sdb2[/FONT]
[FONT=arial]mdadm: /dev/sdb1 is busy - skipping[/FONT]
[FONT=arial]mdadm: no RAID superblock on /dev/sdb[/FONT]
[FONT=arial]mdadm: no RAID superblock on /dev/sda2[/FONT]
[FONT=arial]mdadm: /dev/sda1 is busy - skipping[/FONT]
[FONT=arial]mdadm: no RAID superblock on /dev/sda[/FONT]
[FONT=arial]mdadm: no RAID superblock on /dev/loop0[/FONT]
[FONT=arial]mdadm: looking for devices for /dev/md1[/FONT]
[FONT=arial]mdadm: Cannot assemble mbr metadata on /dev/sde1[/FONT]
[FONT=arial]mdadm: Cannot assemble mbr metadata on /dev/sde[/FONT]
[FONT=arial]mdadm: no RAID superblock on /dev/sdd1[/FONT]
[FONT=arial]mdadm: no RAID superblock on /dev/sdd[/FONT]
[FONT=arial]mdadm: no RAID superblock on /dev/sdc1[/FONT]
[FONT=arial]mdadm: no RAID superblock on /dev/sdc[/FONT]
[FONT=arial]mdadm: no RAID superblock on /dev/sdb1[/FONT]
[FONT=arial]mdadm: no RAID superblock on /dev/sdb[/FONT]
[FONT=arial]mdadm: no RAID superblock on /dev/sda1[/FONT]
[FONT=arial]mdadm: no RAID superblock on /dev/sda[/FONT]
[FONT=arial]mdadm: no RAID superblock on /dev/loop0[/FONT]
[FONT=arial]mdadm: /dev/sdd2 is identified as a member of /dev/md1, slot 0.[/FONT]
[FONT=arial]mdadm: /dev/sdc2 is identified as a member of /dev/md1, slot 3.[/FONT]
[FONT=arial]mdadm: /dev/sdb2 is identified as a member of /dev/md1, slot 1.[/FONT]
[FONT=arial]mdadm: /dev/sda2 is identified as a member of /dev/md1, slot 2.[/FONT]
[FONT=arial]mdadm: added /dev/sdb2 to /dev/md1 as 1[/FONT]
[FONT=arial]mdadm: added /dev/sda2 to /dev/md1 as 2 (possibly out of date)[/FONT]
[FONT=arial]mdadm: added /dev/sdc2 to /dev/md1 as 3 (possibly out of date)[/FONT]
[FONT=arial]mdadm: added /dev/sdd2 to /dev/md1 as 0[/FONT]
[FONT=arial]mdadm: /dev/md1 assembled from 2 drives - not enough to start the array.

I also ran mdadm --examine for each disk and these are the results:

[/FONT][FONT=arial]/dev/sda2:[/FONT]
[FONT=arial]          Magic : a92b4efc[/FONT]
[FONT=arial]        Version : 0.90.00[/FONT]
[FONT=arial]           UUID : 5ff12998:9c1883a2:37651b0a:[/FONT][FONT=arial]3bbd305e[/FONT]
[FONT=arial]  Creation Time : Sun Sep 13 02:27:13 2009[/FONT]
[FONT=arial]     Raid Level : raid5[/FONT]
[FONT=arial]  Used Dev Size : 1463176000 (1395.39 GiB 1498.29 GB)[/FONT]
[FONT=arial]     Array Size : [/FONT][4389528000]("tel:4389528000")[FONT=arial] (4186.18 GiB 4494.88 GB)[/FONT]
[FONT=arial]   Raid Devices : 4[/FONT]
[FONT=arial]  Total Devices : 3[/FONT]
[FONT=arial]Preferred Minor : 1[/FONT]

[FONT=arial]    Update Time : Wed Dec 24 05:44:26 2014[/FONT]
[FONT=arial]          State : clean[/FONT]
[FONT=arial] Active Devices : 3[/FONT]
[FONT=arial]Working Devices : 3[/FONT]
[FONT=arial] Failed Devices : 1[/FONT]
[FONT=arial]  Spare Devices : 0[/FONT]
[FONT=arial]       Checksum : f12e17e - correct[/FONT]
[FONT=arial]         Events : 2019620[/FONT]

[FONT=arial]         Layout : left-symmetric[/FONT]
[FONT=arial]     Chunk Size : 64K[/FONT]

[FONT=arial]      Number   Major   Minor   RaidDevice State[/FONT]
[FONT=arial]this     2       8       34        2      active sync   /dev/sdc2[/FONT]

[FONT=arial]   0     0       8        2        0      active sync   /dev/sda2[/FONT]
[FONT=arial]   1     1       8       18        1      active sync   /dev/sdb2[/FONT]
[FONT=arial]   2     2       8       34        2      active sync   /dev/sdc2[/FONT]
[FONT=arial]   3     3       0        0        3      faulty removed[/FONT]



[FONT=arial]/dev/sdb2:[/FONT]
[FONT=arial]          Magic : a92b4efc[/FONT]
[FONT=arial]        Version : 0.90.00[/FONT]
[FONT=arial]           UUID : 5ff12998:9c1883a2:37651b0a:[/FONT][FONT=arial]3bbd305e[/FONT]
[FONT=arial]  Creation Time : Sun Sep 13 02:27:13 2009[/FONT]
[FONT=arial]     Raid Level : raid5[/FONT]
[FONT=arial]  Used Dev Size : 1463176000 (1395.39 GiB 1498.29 GB)[/FONT]
[FONT=arial]     Array Size : [/FONT][4389528000]("tel:4389528000")[FONT=arial] (4186.18 GiB 4494.88 GB)[/FONT]
[FONT=arial]   Raid Devices : 4[/FONT]
[FONT=arial]  Total Devices : 3[/FONT]
[FONT=arial]Preferred Minor : 1[/FONT]

[FONT=arial]    Update Time : Wed Dec 24 06:21:44 2014[/FONT]
[FONT=arial]          State : clean[/FONT]
[FONT=arial] Active Devices : 2[/FONT]
[FONT=arial]Working Devices : 2[/FONT]
[FONT=arial] Failed Devices : 2[/FONT]
[FONT=arial]  Spare Devices : 0[/FONT]
[FONT=arial]       Checksum : f12ea39 - correct[/FONT]
[FONT=arial]         Events : 2019622[/FONT]

[FONT=arial]         Layout : left-symmetric[/FONT]
[FONT=arial]     Chunk Size : 64K[/FONT]

[FONT=arial]      Number   Major   Minor   RaidDevice State[/FONT]
[FONT=arial]this     1       8       18        1      active sync   /dev/sdb2[/FONT]

[FONT=arial]   0     0       8        2        0      active sync   /dev/sda2[/FONT]
[FONT=arial]   1     1       8       18        1      active sync   /dev/sdb2[/FONT]
[FONT=arial]   2     2       0        0        2      faulty removed[/FONT]
[FONT=arial]   3     3       0        0        3      faulty removed[/FONT]



[FONT=arial]/dev/sdc2:[/FONT]
[FONT=arial]          Magic : a92b4efc[/FONT]
[FONT=arial]        Version : 0.90.00[/FONT]
[FONT=arial]           UUID : 5ff12998:9c1883a2:37651b0a:[/FONT][FONT=arial]3bbd305e[/FONT]
[FONT=arial]  Creation Time : Sun Sep 13 02:27:13 2009[/FONT]
[FONT=arial]     Raid Level : raid5[/FONT]
[FONT=arial]  Used Dev Size : 1463176000 (1395.39 GiB 1498.29 GB)[/FONT]
[FONT=arial]     Array Size : [/FONT][4389528000]("tel:4389528000")[FONT=arial] (4186.18 GiB 4494.88 GB)[/FONT]
[FONT=arial]   Raid Devices : 4[/FONT]
[FONT=arial]  Total Devices : 4[/FONT]
[FONT=arial]Preferred Minor : 1[/FONT]

[FONT=arial]    Update Time : Mon Jan  6 22:40:01 2014[/FONT]
[FONT=arial]          State : active[/FONT]
[FONT=arial] Active Devices : 4[/FONT]
[FONT=arial]Working Devices : 4[/FONT]
[FONT=arial] Failed Devices : 0[/FONT]
[FONT=arial]  Spare Devices : 0[/FONT]
[FONT=arial]       Checksum : d1c7ae6 - correct[/FONT]
[FONT=arial]         Events : 1465695[/FONT]

[FONT=arial]         Layout : left-symmetric[/FONT]
[FONT=arial]     Chunk Size : 64K[/FONT]

[FONT=arial]      Number   Major   Minor   RaidDevice State[/FONT]
[FONT=arial]this     3       8       50        3      active sync   /dev/sdd2[/FONT]

[FONT=arial]   0     0       8        2        0      active sync   /dev/sda2[/FONT]
[FONT=arial]   1     1       8       18        1      active sync   /dev/sdb2[/FONT]
[FONT=arial]   2     2       8       34        2      active sync   /dev/sdc2[/FONT]
[FONT=arial]   3     3       8       50        3      active sync   /dev/sdd2[/FONT]


[FONT=arial]/dev/sdd2:[/FONT]
[FONT=arial]          Magic : a92b4efc[/FONT]
[FONT=arial]        Version : 0.90.00[/FONT]
[FONT=arial]           UUID : 5ff12998:9c1883a2:37651b0a:[/FONT][FONT=arial]3bbd305e[/FONT]
[FONT=arial]  Creation Time : Sun Sep 13 02:27:13 2009[/FONT]
[FONT=arial]     Raid Level : raid5[/FONT]
[FONT=arial]  Used Dev Size : 1463176000 (1395.39 GiB 1498.29 GB)[/FONT]
[FONT=arial]     Array Size : [/FONT][4389528000]("tel:4389528000")[FONT=arial] (4186.18 GiB 4494.88 GB)[/FONT]
[FONT=arial]   Raid Devices : 4[/FONT]
[FONT=arial]  Total Devices : 3[/FONT]
[FONT=arial]Preferred Minor : 1[/FONT]

[FONT=arial]    Update Time : Wed Dec 24 06:21:44 2014[/FONT]
[FONT=arial]          State : clean[/FONT]
[FONT=arial] Active Devices : 2[/FONT]
[FONT=arial]Working Devices : 2[/FONT]
[FONT=arial] Failed Devices : 2[/FONT]
[FONT=arial]  Spare Devices : 0[/FONT]
[FONT=arial]       Checksum : f12ea27 - correct[/FONT]
[FONT=arial]         Events : 2019622[/FONT]

[FONT=arial]         Layout : left-symmetric[/FONT]
[FONT=arial]     Chunk Size : 64K[/FONT]

[FONT=arial]      Number   Major   Minor   RaidDevice State[/FONT]
[FONT=arial]this     0       8        2        0      active sync   /dev/sda2[/FONT]

[FONT=arial]   0     0       8        2        0      active sync   /dev/sda2[/FONT]
[FONT=arial]   1     1       8       18        1      active sync   /dev/sdb2[/FONT]
[FONT=arial]   2     2       0        0        2      faulty removed[/FONT]
[FONT=arial]   3     3       0        0        3      faulty removed


i tried to force assembly but all 4 drives are marked as inactive ( you can clearly tell i dont really know what im doing )

ANY HELP or GUIDANCE would be greatly appreciated!!  THANK YOU![/FONT]

---

### Post by tony66 on 2015-01-06
Also, let me know if this is not the correct forum to ask.  thanks!

---

### Post by whitesmith on 2015-01-06
I know the purpose of this forum is to help users and not devolve into sopomoric shouting and school-yard sarcasm. I therefore pass this along in keeping with the intended spirit of the board--nothing more, nothing less. *Don't use RAID 5.* There is a site ([http://baarf.com](http://baarf.com)) maintained by engineers who have satisfactorily demonstrated to me that the numerous RAID 5 sites I put together actually harmed the owners of the servers. Battle Against Any Raid Five (formerly: Ban All Applications of Raid Five) is this site's motto, and its arguments are cogent. Please give it a peek. I am not connected with it in any way. Good times!

---

### Post by tony66 on 2015-01-08
ran another force and it was able to assemble.  3 out of 4 disks initialized.  im in good shape.

and i will def take a look at that article.  thanks again

---

