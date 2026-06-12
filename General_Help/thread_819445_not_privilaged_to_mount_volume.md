---
title: "not privilaged to mount volume"
date: 2008-06-05
forum: General Help
---

### Post by ChaosMastero on 2008-06-05
When I try to mount a partition on my machine I get an error saying that I don't have privileges to do so.  How do I give myself the privilege to mount it?  I'm using Ubuntu 8.04

---

### Post by mrMango on 2008-06-05
Are you mounting it from the command line? You would need to use sudo to do that.

Also make sure your user is a member of the plugdev group

---

### Post by ChaosMastero on 2008-06-05
I was trying to mount it from the "Computer" window by right clicking on it and selecting "Mount Volume".  I'm logged in as an administrator (or is it called root in Ubuntu?). 

Anyways.  Before I upgraded I was able to read from the other NTFS partitions but not write.  Now I can't even read them (but they work fine for Windows).

---

### Post by Zer0Nin3r on 2008-06-09
I'm experiencing the same problem too.  Was working a couple of days ago I know that.  I don't know if it's because of recent crashes that have been happening or if it was an update I recently installed.  Any help would be greatly appreciated.  Thanks!

---

### Post by PmDematagoda on 2008-06-09
> **Zer0Nin3r said:**
> I'm experiencing the same problem too.  Was working a couple of days ago I know that.  I don't know if it's because of recent crashes that have been happening or if it was an update I recently installed.  Any help would be greatly appreciated.  Thanks!

Post the output of:-
```
fdisk -l
```
and if possible, point out the drive/partition that is the culprit. Else, post the output of:-
```
cat /etc/mtab
```

---

### Post by Zer0Nin3r on 2008-06-09
Here are the outputs of the commands 'fdisk -l' and 'cat /etc/mtab'

Also I ran Nautilus in sudo from terminal and tried accessing the partitions through there without any luck.  I was able to get a screen shot of the error as it gave me details under sudo that I wasn't getting under normal access.  See attachment.

After reading the error details...come to think of it Windows did recently freeze up on me and I was unable to safely shut down.  I'll reboot and see if that solves the problem.

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x335e335d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1946    15631213+   7  HPFS/NTFS
/dev/sda2            6081       27434   171526005    f  W95 Ext'd (LBA)
/dev/sda3            1947        6080    33206355   83  Linux
/dev/sda4           27435       30401    23832427+  83  Linux
/dev/sda5            6081       27361   170939601    7  HPFS/NTFS
/dev/sda6           27362       27434      586341   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31e909a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

```

```
/dev/sda3 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-18-generic/volatile tmpfs rw 0 0
/dev/sda4 /media ext3 rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0

```

---

### Post by PmDematagoda on 2008-06-09
Do this:-
```
sudo apt-get install ntfsprogs
```
after that is installed do:-
```
sudo ntfsfix /dev/sda5
```

The drive should now mount properly.

---

### Post by Zer0Nin3r on 2008-06-09
Solved the problem for myself.  It turns out that it was in fact a problem related to the system crash in WinXP.  Booted up, ran some programs and shut down normally.  Seemed to fix the problem.  Thanks for the help and insight!!

---

