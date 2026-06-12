---
title: "[SOLVED] blinking cursor after splash screen"
date: 2008-05-26
forum: General Help
---

### Post by MythosLegend on 2008-05-26
**Solved**
Hi. 
I get a splash screen when I boot up. I can never get to the login screen. The blank screen with a blinking cursor shows after the splash.

I am able to go into recovery mode and also use the live cd.

When I go into recovery mode, I got one failed message. 

Mounting local filesystems
Failed to access 'dev/disk/by-uuid/7098717298713824': no such file or directory

I checked out my fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=6bbbc34d-94eb-43f3-ac98-e8d381c531f2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=7098717298713824 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda5
UUID=FA60CCEF60CCB423 /media/hda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda2
UUID=8eeb1a42-cbf3-42b6-864c-6cb7c193fa04 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

The culprit is ntfs partition (WinXP). The WinXP works because I'm able to log into it. When I try to access a linux partition with ext2ifs, it says the partition is empty (and do I want to format it).

I did a vol_id on /dev/hda1 and changed the uuid to AA2C461C2C45E3C3.

The partition now mounts correctly. I still get the same problem. 

I'm out of ideas. I'm willing to crash the ubuntu system in the process of solving this issue.

fdisk -l results:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1306    10490413+   7  HPFS/NTFS
/dev/hda2            1307        1437     1052257+  82  Linux swap / Solaris
/dev/hda3            1438        4863    27519345    f  W95 Ext'd (LBA)
/dev/hda4            2613        4863    18081126    7  HPFS/NTFS
/dev/hda5            1438        2612     9438124+  83  Linux

```
**Solved**

_Solution_: 
Time: Many hours later. 
I kept logging into recovery mode and noticed that nfs utilities would take longest to load. On the shutdown portmap daemon would sometimes get stuck. NFS is dependent on portmap. I had to use the live cd to reinstall portmap.  I don't even use this utility. Go Figure.:mad:

---

