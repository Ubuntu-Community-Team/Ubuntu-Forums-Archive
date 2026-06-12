---
title: "Harddisk space missing in Ubuntu"
date: 2007-05-04
forum: General Help
---

### Post by maq on 2007-05-04
Hi everyone,

I have a problem i hope you can help me with. I have a harddisk on about 60 gb but I am unable to access about 10 gb of the disk. When I view my layout through gparted the /-partition should be 13.9 gb but when I view it through the System Monitor or df only 3.9 gb is available.

```

***@***:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             3,9G  2,9G  898M  77% /
varrun                760M  292K  759M   1% /var/run
varlock               760M     0  760M   0% /var/lock
procbususb            760M  140K  760M   1% /proc/bus/usb
udev                  760M  140K  760M   1% /dev
devshm                760M     0  760M   0% /dev/shm
lrm                        760M   33M  727M   5% /lib/modules/2.6.20-15-generic/volatile
/dev/sda4              37G   32G  2,6G  93% /home
/dev/sdb1              92G   35G   53G  41% /media/Files
/dev/sda2             3,8G  3,6G  194M  95% /media/SERVICEV001

```

When I run fdisk I get the following.

```

***@***:~$ sudo fdisk /dev/sda -l
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         187     1502046   82  Linux swap / Solaris
/dev/sda2            6807        7296     3923640   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda3             188        2011    14651280   83  Linux
/dev/sda4            2012        6806    38515837+  83  Linux

Partition table entries are not in disk order

```

Does anyone have a clue about what's going on? Will I have to reinstall my system?


Greetings!
Kaspar

---

### Post by crispy_420 on 2007-05-05
Looks like a Compaq restore partition to me. I don't know about deleting it though and if it is possible to add to exsisting install as anything but an additional drive.

---

