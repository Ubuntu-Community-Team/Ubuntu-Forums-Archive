---
title: "du and df commands give contradictory outputs"
date: 2015-12-04
forum: General Help
---

### Post by sebastiaopburnay on 2015-12-04
Hey!

I have an Ubuntu Server 12.04 LTS (64bit version),

My filesystem is organized in partitions and one of them is used for logging purposes (/dev/sdb mounted on /var/log).

Somehow when I run df I get information that my log partition is at 100% of its 7GB capacity and by running du I find it is only using a few hundred kB, it makes no sense.

Even when I'm just listing the /var/log content with 'ls -lh' I do not find many files:
```
root@MYSERVER:/# sudo du --max-depth=1 -x -h /var/log/
4.0K    /var/log/news
12K     /var/log/mysql
76K     /var/log/apache2
16K     /var/log/lost+found
4.0K    /var/log/sysstat
4.0K    /var/log/apt
4.0K    /var/log/landscape
816K    /var/log/
```
```
root@MYSERVER:/# df -h | grep log
Filesystem                        Size  Used Avail Use% Mounted on
/dev/sdb                          7.0G  6.7G   24M 100% /var/log
```

Thank you in advance for your help

---

### Post by efflandt on 2015-12-04
How is /dev/sdb partitioned/formatted? Normally /dev/sdb would be a "drive" and /dev/sdb1 would be the first "partition" on that drive. Or did you format /dev/sdb with no partitions (like a floppy)?

---

### Post by sebastiaopburnay on 2015-12-07
> **efflandt said:**
> How is /dev/sdb partitioned/formatted? Normally /dev/sdb would be a "drive" and /dev/sdb1 would be the first "partition" on that drive. Or did you format /dev/sdb with no partitions (like a floppy)?

Hey!

Thanks for your advice, but I have no mount points within /var/log nor my /dev/sdb is partitioned.

I've tried "fsck -f /dev/sdb" and it identified/corrected a few issues:
[LIST]
[*]several "Free blocks count wrong (98036, counted=1769110)"
[*]Orphaned inodes
[/LIST]

The result from fsck:
```
/dev/sdb: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sdb: 44/458752 files (11.4 non-contiguous), 65898/1835008 blocks

```

The partition remains accusing 100%

Yet, after another reboot, it went to 4% used which is the correct value

---

