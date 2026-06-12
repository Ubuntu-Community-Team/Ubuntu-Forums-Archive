---
title: "no gnome icon for an ntfs drive (others Ok)"
date: 2007-10-18
forum: General Help
---

### Post by sporto on 2007-10-18
Hi All,

I'm running gutsy and Gnome doesn't create an icon for one of my NTFS drives.

I can access the drive in the terminal fine. sudo mount -a gives no errors. The problem drive is sde1 / xpdocs.

Thanks in advance for any tips!

df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/md1              457G  2.8G  431G   1% /
varrun                2.0G   88K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  136K  2.0G   1% /dev
devshm                2.0G     0  2.0G   0% /dev/shm
lrm                   2.0G   38M  1.9G   2% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb1             942M   36M  859M   4% /boot
/dev/sdc1             942M   18M  877M   2% /tmp
/dev/sdd1             9.8G  5.6G  4.3G  57% /media/windows
/dev/sdd2             224G   89G  135G  40% /media/xpprograms
/dev/sde1             233G   87G  147G  38% /media/xpdocs
/dev/sdf1             233G   72M  233G   1% /media/xpworking

fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md1
UUID=05daab38-fa67-4890-aae6-18853180ff8b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb1
UUID=a69c7ed6-f310-43d4-ab5e-de6b451e0b7c /boot           ext3    defaults        0       2
# /dev/sdc1
UUID=cc3de0a6-89be-485e-ada2-26f6da109724 /tmp            ext3    defaults        0       2
# /dev/sda1
UUID=7a209765-8b51-471f-9eb9-b6bb2c6ea09c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

/dev/sdd1    /media/windows ntfs  nls=utf8,umask=0222 0    0
/dev/sdd2    /media/xpprograms ntfs  nls=utf8,umask=0222 0    0
/dev/sde1    /media/xpdocs ntfs  nls=utf8,umask=0222 0    0
/dev/sdf1    /media/xpworking ntfs  nls=utf8,umask=0222

---

### Post by dustman on 2008-01-14
yeah i'm having the same problem...i installed all sort of stuff and now i don't have any icons for my NTFS partitions. If i plug in a USB stick, it get's recognized, and a Nautilus window pops out...but again, no icon on the desktop (like it was before the installations). 

Anyone has any ideas? 

Cheers!


Radu



[EDIT] I was a bit hasty with this post last night. All i had to do was a system restart, and everything went back to normal :). My bad!

---

