---
title: "45GB gone missing!"
date: 2007-05-08
forum: General Help
---

### Post by TheJackal on 2007-05-08
Hi,

  I have a weird problem..about 45GB of disk space is unaccounted and missing.

  DF shows 68GB used but DU only shows 25GB used.  There is about 45GB missing.  I have tried to find the missing files using Babboa, but it yields the same result.

   Could anyone help me and enlighten me where else should I look?  I ran of ideas.  Appreciate any help.  Thanks in advance.


Exact Results:
========
df -h
     
    Filesystem            Size  Used Avail Use% Mounted on
    /dev/hdb1              74G   68G  2.6G  97% /
    varrun                188M  156K  188M   1% /var/run
    varlock               188M  4.0K  188M   1% /var/lock
    udev                  188M  112K  188M   1% /dev
    devshm                188M     0  188M   0% /dev/shm
    lrm                   188M   19M  170M  10% /lib/modules/2.6.15-28-386/volatile
    /dev/hda1             9.1G  607M  8.0G   7% /boot
    /dev/sda5              73G   30G   40G  43% /backup
    /dev/sda1              20G  272K   20G   1% /media/USBDRIVE

du -hs /*

    30G     /backup
    4.3M    /bin
    479M    /boot
    0       /cdrom
    128K    /dev
    13M     /etc
    24G     /home
    4.0K    /initrd
    0       /initrd.img
    0       /initrd.img.old
    344M    /lib
    48K     /lost+found
    284K    /media
    4.0K    /mnt
    4.0K    /opt
    385M    /proc
    160K    /root
    11M     /sbin
    4.0K    /srv
    0       /sys
    52K     /tmp

---

### Post by taurus on 2007-05-08
```
sudo du -h /
```

---

### Post by TheJackal on 2007-05-08
No help.  The last 2 lines shows:

30G	/backup
56G	/

Which means 26G is used in total for root...but where is the other 45GB?

Any more ideas?

---

### Post by pirothezero on 2007-05-08
sudo fdisk -l

---

### Post by dasunst3r on 2007-05-08
Can you still see the files in your file management program?

---

### Post by TheJackal on 2007-05-08
sudo fdisk -l results:

Disk /dev/hda: 10.2 GB, 10239860736 bytes
255 heads, 63 sectors/track, 1244 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1199     9630936   83  Linux
/dev/hda2            1200        1244      361462+   5  Extended
/dev/hda5            1200        1244      361431   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9729    78148161   83  Linux

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/sda2            2551       12161    77200357+   f  W95 Ext'd (LBA)
/dev/sda5            2551       12161    77200326    6  FAT16

---

### Post by TheJackal on 2007-05-08
> **dasunst3r said:**
> Can you still see the files in your file management program?
Yes, I can see all those files that are accounted for..just not those unaccounted ones..which is 45GB in total.

---

### Post by rai4shu2 on 2007-05-08
Isn't du including /backup and /boot in its / calculation?

---

### Post by TheJackal on 2007-05-08
Yes, it includes.  But that's not the problem.  It's in /backup..which is on another disk which has 80GB.  All the space in that disk (sda1) is accounted for. It's /dev/hdb1 that I am having problem with.

---

### Post by rai4shu2 on 2007-05-08
Maybe it's really fragmented.

---

### Post by TheJackal on 2007-05-08
Not likely.  I did apt-get clean, fsck -f, and everything turns out fine.

---

### Post by Slim Odds on 2007-05-08
Try using the -x option for du

---

### Post by TheJackal on 2007-05-08
It didn't help.  I am suspecting could it be swap files used by some processes?  However, when I do a lsof, I don't see anything.

---

### Post by taurus on 2007-05-08
Can you post

```
cat /etc/fstab
```

---

### Post by TheJackal on 2007-05-08
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by taurus on 2007-05-08
Did you mount both /dev/sda1 & /dev/sda5 by hand?  Try

```
sudo umount /dev/sda1 /dev/sda5
df -h
sudo du -h /
```
Post the output of the last two commands here.

---

### Post by TheJackal on 2007-05-08
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1              74G   68G  2.6G  97% /
varrun                188M  388K  188M   1% /var/run
varlock               188M  4.0K  188M   1% /var/lock
udev                  188M  112K  188M   1% /dev
devshm                188M     0  188M   0% /dev/shm
lrm                   188M   19M  170M  10% /lib/modules/2.6.15-28-386/volatile
/dev/hda1             9.1G  607M  8.0G   7% /boot

```

The du -h list was too long..so i did a du -hs instead:

```

42G     /backup
4.3M    /bin
479M    /boot
0       /cdrom
128K    /dev
13M     /etc
24G     /home
4.0K    /initrd
0       /initrd.img
0       /initrd.img.old
344M    /lib
48K     /lost+found
16K     /media
4.0K    /mnt
4.0K    /opt
385M    /proc
160K    /root
11M     /sbin
4.0K    /srv
0       /sys
52K     /tmp

```

Is it correct that /backup still there when I have umounted it?

---

### Post by taurus on 2007-05-08
```
cd /backup
ls -la 
```

---

### Post by TheJackal on 2007-05-08
```
total 20
drwxr-xr-x  5 root root 4096 2007-04-28 02:30 .
drwxr-xr-x 22 root root 4096 2007-04-18 17:59 ..
drwxr-xr-x  2 root root 4096 2007-04-21 02:30 20070421
drwxr-xr-x  2 root root 4096 2007-04-28 02:30 20070428
drwxr-xr-x 10 root root 4096 2007-05-01 23:50 myob

```
It's all my backup files.  Doesn't look anything funny.

This is the du -hs:

```

21G     /backup/20070421
21G     /backup/20070428
14M     /backup/myob

```

---

### Post by taurus on 2007-05-08
> **TheJackal said:**
> 
```

[B][COLOR="Red"]21G     /backup/20070421
21G     /backup/20070428[/COLOR][/B]
14M     /backup/myob

```

You may want to remove those two directories then since they are a backup of your system.

```
cd /backup
sudo rm -rf  20070421  20070428
df -h
```
Then, you need to look in /etc/cron.weekly because there is a script to do a backup of your system weekly, taking up space on your /dev/hdb1.

---

### Post by TheJackal on 2007-05-08
It works!  But I am curious why /backup is part of hdb1 when clearly I have mounted as /backup?  Many thanks!

---

### Post by taurus on 2007-05-08
And what was why I asked you how you mounted both /dev/sda1 & /dev/sda5 in my previous reply.

---

