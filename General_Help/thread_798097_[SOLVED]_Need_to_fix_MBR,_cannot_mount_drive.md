---
title: "[SOLVED] Need to fix MBR, cannot mount drive"
date: 2008-05-17
forum: General Help
---

### Post by smo0th on 2008-05-17
This is really strange, my computer was running perfectly a couple of days ago and one morning my keyboard fell, after few seconds the computer turned off just like that, no chance to view anything in the screen, is there a key combination that could lead to this kind of problem? Is there a way to prevent it from happening again?

Anyway, I tried testdisk and found something weird, please look at the attached screen shot. The primary bootable partition appears duplicated, however, when using quick and deeper search, partitions appear good.

I wrote again the partition information and rebooted to see if something changed but the same behavior prevails, when I try to mount the partition I get the following:

```

root@ubuntu:~# mount -t ext3 /dev/sda1 /media/ubuntu
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@ubuntu:~# dmesg |tail
[  122.500266] NET: Registered protocol family 17
[  130.660370] NET: Registered protocol family 10
[  130.660577] lo: Disabled Privacy Extensions
[  130.661357] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  139.020251] hda-intel: Invalid position buffer, using LPIB read method instead.
[  140.889314] eth0: no IPv6 routers present
[  456.979234] cdrom: hda: mrw address space DMA selected
[ 1636.196628] VFS: Can't find ext3 filesystem on dev sda1.
[ 1646.761624] VFS: Can't find ext3 filesystem on dev sda1.
[ 2887.026893] VFS: Can't find ext3 filesystem on dev sda1.
root@ubuntu:~# 

```

And the output from fdisk is:
```

root@ubuntu:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000679c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60680   487412068+  83  Linux
/dev/sda2           60681       60801      971932+  82  Linux swap / Solaris

Disk /dev/hdb: 15.3 GB, 15367790592 bytes
255 heads, 63 sectors/track, 1868 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f1842cc

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1867    14996646    7  HPFS/NTFS
root@ubuntu:~# 

```

BTW: I have checked the BIOS settings and tried all possible configurations that may work, still nothing, besides it was working before anyway.

Now, things got a step worse, when using testdisk I messed up the MBR and got a prompt that does nothing.

I need to fix my MBR and make GRUB recognize my partitions, I have tried everything in [this]("http://ubuntuforums.org/showthread.php?t=752588") post and some others but still no luck.

H E L P  :frown:

---

### Post by smo0th on 2008-05-19
Great, although no one posted a reply to this thread, there's a solution in [this other]("http://ubuntuforums.org/showthread.php?t=752588") thread, so I'll mark this one as solved.

Hope this helps someone :)

---

