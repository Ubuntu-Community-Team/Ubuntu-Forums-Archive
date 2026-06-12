---
title: "I cant find SDA1"
date: 2007-11-11
forum: General Help
---

### Post by Xora on 2007-11-11
I have a dual boot, and up untill recently I could go through all my Windows Partition while in Ubuntu. Its was called SDA1 or something similar. I no longer can find it and Windows cant find the Ubuntu partition. Please help!

---

### Post by scxtt on 2007-11-11
what's the output of **sudo fdisk -l**?

---

### Post by Xora on 2007-11-11
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4865    39078081    7  HPFS/NTFS
/dev/sda2            4866        4896      249007+  82  Linux swap / Solaris
/dev/sda3            4897        9729    38821072+  83  Linux

Anything helpfull?

---

### Post by Xora on 2007-11-11
Might help to say that I know little to nothing about linux.

---

### Post by scxtt on 2007-11-11
what's the output of the following 2 commands?:

mount
cat /etc/fstab

---

### Post by Xora on 2007-11-11
xora@xora-laptop:~$ mount
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)


xora@xora-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=96859af5-15e7-4c84-bf86-b368aa792950 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=F4E0AAEFE0AAB770 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=c340425e-7594-452a-9bbc-0184d30121d6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


And If you get a moment what do those commands mean?

---

### Post by noynac on 2007-11-11
I just had the same problem. Turns out I hadn't shut down Windows properly. See the following thread:

[http://ubuntuforums.org/showthread.php?t=593329&highlight=windows+fstab](http://ubuntuforums.org/showthread.php?t=593329&highlight=windows+fstab)

---

### Post by Xora on 2007-11-12
Wow, thank you, I hadnt considered that!
It worked!

---

