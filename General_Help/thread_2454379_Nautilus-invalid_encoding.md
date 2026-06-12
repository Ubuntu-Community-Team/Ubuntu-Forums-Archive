---
title: "Nautilus-invalid encoding"
date: 2020-11-28
forum: General Help
---

### Post by Freiklite on 2020-11-28
Hi,
Nautilus shows "invalid encoding" for some files with special characters.
The files are remount as read-only.
The others are without rw problem.

Some information:
[HTML]~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=d95d3765-76ae-4388-893e-cc0e823f55f6 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=4D9D-7FE8  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

[/HTML]

[HTML]~$ cat /etc/mtab | grep sdb
/dev/sdb1 /media/dominique/STORE\040N\040GO vfat rw,sync,nosuid,nodev,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro 0 0

[/HTML]
[HTML]~$ locale -a | grep fr
fr_BE.utf8
fr_CA.utf8
fr_CH.utf8
fr_FR.utf8
fr_LU.utf8

[/HTML]

[HTML]
$ sudo fdisk -l
***
Disque /dev/sdb : 14,76 GiB, 15833497600 octets, 30924800 secteurs
Disk model: ProductCode     
Unités : secteur de 1 × 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Type d'étiquette de disque : dos
Identifiant de disque : 0x03855c1b

Périphérique Amorçage Début      Fin Secteurs Taille Id Type
/dev/sdb1    *           64 30924799 30924736  14,8G  b W95 FAT32

[/HTML]


Thank you very much for your attention.
You will be a great help to me.
Bye.

---

