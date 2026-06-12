---
title: "mount permissions"
date: 2006-10-10
forum: General Help
---

### Post by dgel on 2006-10-10
Hi

I thought this would be well documented by now, but i really can't figure out how to mount anything as a user. i can do so as root, but then i can't easily access the files (i'm a new user of linux and don't even know how to get in a folder that i don't own in the terminal :-\" "sudo cd /" doesnt work^^)
so how can one do this? i really need to get to files on a usb disk...

thanks

Na-Fiann

---

### Post by aysiu on 2006-10-10
Can you plug in the USB disk and post the output of these [terminal](http://www.psychocats.net/ubuntu/terminal) commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
``` You can just copy and paste those into the terminal--no need to retype them.

---

### Post by dgel on 2006-10-10
sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1844    14811898+   7  HPFS/NTFS
/dev/hda2            1845       14593   102406342+   f  W95 Ext'd (LBA)
/dev/hda5            1845        4066    17848183+   7  HPFS/NTFS
/dev/hda6   *        4067        4743     5437971   83  Linux
/dev/hda7            4744        4777      273073+  82  Linux swap / Solaris
/dev/hda8            4778        7964    25599546    b  W95 FAT32
/dev/hda9            7972       11159    25607578+   b  W95 FAT32
/dev/hda10          11181       14593    27414891    b  W95 FAT32

Disk /dev/sda: 4095 MB, 4095737856 bytes
126 heads, 62 sectors/track, 1024 cylinders
Units = cylinders of 7812 * 512 = 3999744 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?       99608      245731   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(99607, 97, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(245730, 44, 51)
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?       21594      269422   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(21593, 80, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(269421, 14, 42)
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?      239361      487188   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(239360, 18, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(487187, 77, 39)
Partition 3 does not end on cylinder boundary.
/dev/sda4   ?      369391      369398       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(369390, 104, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(369397, 117, 33)
Partition 4 does not end on cylinder boundary.

df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda6             5.2G  4.1G  768M  85% /
varrun                506M   92K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  132K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   19M  488M   4% /lib/modules/2.6.15-27-386/volatile
/dev/hda10             27G   25G  1.3G  96% /media/hda10
/dev/hda5              18G   12G  5.8G  67% /media/hda5
/dev/hda8              25G   17G  8.3G  67% /media/hda8
/dev/hda9              25G   17G  7.6G  70% /media/hda9
/dev/sda              3.9G  111M  3.7G   3% /media/usbdisk

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda10      /media/hda10    vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda8       /media/hda8     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda9       /media/hda9     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda7       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0


right now the disk is mounted as root using sudo.

---

### Post by aysiu on 2006-10-10
This looks like the problem. ```
Disk /dev/sda: 4095 MB, 4095737856 bytes
126 heads, 62 sectors/track, 1024 cylinders
Units = cylinders of 7812 * 512 = 3999744 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

Device Boot Start End Blocks Id System
/dev/sda1 ? 99608 245731 570754815+ 72 Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
phys=(357, 116, 40) logical=(99607, 97, 11)
Partition 1 has different physical/logical endings:
phys=(357, 32, 45) logical=(245730, 44, 51)
Partition 1 does not end on cylinder boundary.
/dev/sda2 ? 21594 269422 968014120 65 Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
phys=(288, 115, 43) logical=(21593, 80, 47)
Partition 2 has different physical/logical endings:
phys=(367, 114, 50) logical=(269421, 14, 42)
Partition 2 does not end on cylinder boundary.
/dev/sda3 ? 239361 487188 968014096 79 Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
phys=(366, 32, 33) logical=(239360, 18, 30)
Partition 3 has different physical/logical endings:
phys=(357, 32, 43) logical=(487187, 77, 39)
Partition 3 does not end on cylinder boundary.
/dev/sda4 ? 369391 369398 27749+ d Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
phys=(372, 97, 50) logical=(369390, 104, 25)
Partition 4 has different physical/logical endings:
phys=(0, 10, 0) logical=(369397, 117, 33)
Partition 4 does not end on cylinder boundary.
``` It's missing a valid partition table, apparently.

---

