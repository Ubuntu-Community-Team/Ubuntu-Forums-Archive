---
title: "Only folders, all files are gone"
date: 2013-01-19
forum: General Help
---

### Post by frager on 2013-01-19
Xubuntu 12.04

After I changed the master / slave settings of my two IDE harddisks, my system would abort the boot process after the bios messages with "error: file not found" and a grub rescue prompt.

I booted from a KNOPPIX live cd, mounted my original system partition /dev/sda1 and tried the  following in order to repair grub:

```
root@Microknoppix:/media# changeroot /sda1
bash: changeroot: Kommando nicht gefunden.
```Sorry, this is a Geman live CD, Kommando nicht gefunden means command not found.
In the following, I give you some more interesting outputs. Can anyone help? Thanks.

```
root@Microknoppix:/media# ls sda1/bin/       
root@Microknoppix:/media# ls -a sda1
.   bin   datenFAT  etc  home  lost+found  mnt  proc  run   selinux  sys  usr  windoof
..  boot  dev       gbh  lib   media       opt  root  sbin  srv      tmp  var
root@Microknoppix:/media# ls -a sda1/boot/
.  ..  extlinux  grub

```All my folders are there but no files, that's why /bin/bash was not found. On the other partitions on the disk, files are present and can be read.

```
root@Microknoppix:/media# df -h
Dateisystem          Größe Benut  Verf Ben% Eingehängt auf
/dev/sr0              691M  691M     0 100% /mnt-system
tmpfs                 1,0G  2,0M 1023M   1% /ramdisk
/dev/cloop            1,9G  1,9G     0 100% /KNOPPIX
unionfs               1,0G  2,0M 1023M   1% /UNIONFS
unionfs               1,0G  2,0M 1023M   1% /home
tmpfs                  10M   52K   10M   1% /UNIONFS/var/run
tmpfs                  10M     0   10M   0% /UNIONFS/var/lock
tmpfs                 100M   56K  100M   1% /UNIONFS/var/log
tmpfs                 1,0G   32K  1,0G   1% /tmp
udev                   20M  316K   20M   2% /dev
tmpfs                 1,0G  4,0K  1,0G   1% /dev/shm
/dev/sda1              19G  278M   18G   2% /media/sda1
/dev/sdc1             489M   56M  433M  12% /media/sdc1
root@Microknoppix:/media# du -sh sda1
106M    sda1
```There is alarmingly little used disk space on sda1. This used to be some 10G.

```
root@Microknoppix:/media# umount sda1
root@Microknoppix:/media# fsck /dev/sda1
fsck from util-linux-ng 2.16.1
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda1: sauber, 23979/1218224 Dateien, 147427/4863670 Blöcke

```Sauber means clean. There seems to be nothing wrong... Who can help? Thanks.

---

### Post by rnerwein on 2013-01-20
> **frager said:**
> Xubuntu 12.04

After I changed the master / slave settings of my two IDE harddisks, my system would abort the boot process after the bios messages with "error: file not found" and a grub rescue prompt.

I booted from a KNOPPIX live cd, mounted my original system partition /dev/sda1 and tried the  following in order to repair grub:

```
root@Microknoppix:/media# changeroot /sda1
bash: changeroot: Kommando nicht gefunden.
```Sorry, this is a Geman live CD, Kommando nicht gefunden means command not found.
In the following, I give you some more interesting outputs. Can anyone help? Thanks.

```
root@Microknoppix:/media# ls sda1/bin/       
root@Microknoppix:/media# ls -a sda1
.   bin   datenFAT  etc  home  lost+found  mnt  proc  run   selinux  sys  usr  windoof
..  boot  dev       gbh  lib   media       opt  root  sbin  srv      tmp  var
root@Microknoppix:/media# ls sda1/boot/
.  ..  extlinux  grub

```All my folders are there but no files, that's why /bin/bash was not found.

```
root@Microknoppix:/media# df -h
Dateisystem          Größe Benut  Verf Ben% Eingehängt auf
/dev/sr0              691M  691M     0 100% /mnt-system
tmpfs                 1,0G  2,0M 1023M   1% /ramdisk
/dev/cloop            1,9G  1,9G     0 100% /KNOPPIX
unionfs               1,0G  2,0M 1023M   1% /UNIONFS
unionfs               1,0G  2,0M 1023M   1% /home
tmpfs                  10M   52K   10M   1% /UNIONFS/var/run
tmpfs                  10M     0   10M   0% /UNIONFS/var/lock
tmpfs                 100M   56K  100M   1% /UNIONFS/var/log
tmpfs                 1,0G   32K  1,0G   1% /tmp
udev                   20M  316K   20M   2% /dev
tmpfs                 1,0G  4,0K  1,0G   1% /dev/shm
/dev/sda1              19G  278M   18G   2% /media/sda1
/dev/sdc1             489M   56M  433M  12% /media/sdc1
root@Microknoppix:/media# du -sh sda1
106M    sda1
```There is alarmingly little used disk space on sda1. This used to be some 10G.

```
root@Microknoppix:/media# umount sda1
root@Microknoppix:/media# fsck /dev/sda1
fsck from util-linux-ng 2.16.1
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda1: sauber, 23979/1218224 Dateien, 147427/4863670 Blöcke

```Sauber means clean. There seems to be nothing wrong... Who can help? Thanks.
hi
let us see the mount options - mount your drive and then type: mount
post the output of this command to see how the device is mounted.
cheers

---

### Post by frager on 2013-01-20
> **rnerwein said:**
> hi
let us see the mount options - mount your drive and then type: mount
post the output of this command to see how the device is mounted.
cheers

```
root@Microknoppix:/media# mount
rootfs on / type rootfs (rw,relatime)
proc on /proc type proc (rw,relatime)
sysfs on /sys type sysfs (rw,relatime)
/dev/sr0 on /mnt-system type iso9660 (ro,relatime)
tmpfs on /ramdisk type tmpfs (rw,relatime,size=1048576k)
/dev/cloop on /KNOPPIX type iso9660 (ro,relatime)
unionfs on /UNIONFS type aufs (rw,relatime,si=831741d,noplink)
unionfs on /home type aufs (rw,relatime,si=831741d,noplink)
usbfs on /proc/bus/usb type usbfs (rw,relatime)
tmpfs on /UNIONFS/var/run type tmpfs (rw,relatime,size=10240k)
tmpfs on /UNIONFS/var/lock type tmpfs (rw,relatime,size=10240k)
tmpfs on /UNIONFS/var/log type tmpfs (rw,relatime,size=102400k)
tmpfs on /tmp type tmpfs (rw,relatime,size=1048576k)
udev on /dev type tmpfs (rw,relatime,size=20480k)
tmpfs on /dev/shm type tmpfs (rw,relatime,size=1048576k)
devpts on /dev/pts type devpts (rw,relatime,mode=1777)
/dev/sda1 on /media/sda1 type ext3 (rw,nosuid,nodev,relatime,errors=continue,data=writeback)
/dev/sda3 on /media/sda3 type ext4 (rw,relatime,barrier=1,data=ordered)
/dev/sdb3 on /media/sdb3 type ext3 (rw,relatime,errors=continue,data=writeback)

```sda3 is an old home partition that I do not use any more and sdb3 is my current home partition. On both of them, files are present and can be read.
Cheers

---

