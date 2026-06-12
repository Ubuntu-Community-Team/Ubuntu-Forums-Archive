---
title: "windows partition no longer accessable after kubuntu reboot"
date: 2007-02-03
forum: General Help
---

### Post by maddbaron on 2007-02-03
The problem has been solved.


I don't know what happened.
I rebooted my kubuntu 6.10 and now all my links to my windows partiton where i keep files are gone and i cant access them through konq. I opened gparted and the space is there hda2 but I cannot access them or that drive at all anymore it says that link doesn't exist anymore.

i have some important files there is there anyway to access them please?

---

### Post by jbtito03 on 2007-02-03
Did you try to mount them manually? What kernel module are you running for NTFS partitions?

---

### Post by maddbaron on 2007-02-03
how do I mount them manually? It  was working correctly since july and after i upgraded to edgy. I pressed end session to start a new one and now I can't access them.

How do I find the kernal?

I typed this into konsole and here is what I got, I think its mounted?

> maddbaron@baronworks:~$ sudo fdisk -l
Password:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         383     3076416   12  Compaq diagnostics
/dev/hda2   *         384        3828    27671962+   c  W95 FAT32 (LBA)
/dev/hda3            3829        3892      514080   82  Linux swap / Solaris
/dev/hda4            3893        7296    27342630   83  Linux

maddbaron@baronworks:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4
UUID=531a5675-91ee-4198-ade2-3be117831552 /               ext3    defaults,error                                                               s=remount-ro 0       1
# /dev/hda1
UUID=3007-17F2  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=320D-180E  /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=58a4511c-0605-4c1f-aa9c-b414a989d447 none            swap    sw                                                                             0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/floppy0  auto    rw,user,noauto  0       0






what do I do next please?

---

### Post by maddbaron on 2007-02-03
I fixed it. I looked at how to mount since you gave me the idea, I assumed it was mounted since gparted saw it but i unmounted itself. I remounted it and now it all works!...

Thank you!

---

### Post by bodhi.zazen on 2007-02-03
Open a terminal

Enter: ```
sudo mount /dev/hda2
```

Post any error message ...

---

