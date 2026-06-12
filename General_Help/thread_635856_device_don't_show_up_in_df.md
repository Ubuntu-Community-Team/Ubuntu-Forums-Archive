---
title: "device don't show up in df"
date: 2007-12-09
forum: General Help
---

### Post by zkab on 2007-12-09
I have installed Ubuntu 7.10 from CD on a SATA-drive:
Everthing seemed OK until I looked at the drive with GParted which complained about missing mountpoint.

fdisk -l gives:

Device Boot Start End Blocks Id System
/dev/sda1 * 1 60424 485355748+ 83 Linux
/dev/sda2 60425 60801 3028252+ 5 Extended
/dev/sda5 60425 60801 3028221 82 Linux swap / Solaris

/etc/fstab gives:

# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=0e21f8c5-6e90-4434-96dc-d98a0b9ce7ee / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5
UUID=ca1df9d2-e38d-4ef4-830a-d63ea1be4426 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

but ...

df -h gives:

Filesystem            Size  Used Avail Use% Mounted on
varrun                505M  240K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M   72K  505M   1% /dev
devshm                505M     0  505M   0% /dev/shm
lrm                   505M   34M  471M   7% /lib/modules/2.6.22-14-generic/volatile


Where is /dev/sda1 in df listing :confused:

Someting is very wrong but I can't figure out how to correct it ...

---

