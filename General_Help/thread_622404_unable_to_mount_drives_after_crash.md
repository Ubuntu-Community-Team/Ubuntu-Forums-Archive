---
title: "unable to mount drives after crash"
date: 2007-11-24
forum: General Help
---

### Post by Chymera on 2007-11-24
Like it usually does these days, my ubuntu locked up half an hour ago; and after having to restart it with rseiub, I got the following:

> [...]
Check disk failed
fsck.ext3: unable to resolve "UUID=&&=aa....."
fsck died with exit status 8

(wasn't able to copy paste it so it isn't that accurate in wording...)
Now, after the error message i get a terminal session, in which, if I type reboot i can start my ubuntu gdm.... however I cannot mount any partition except usb drives and my filesystem...

Any ideas on how to get things going again? Being able to mount the hdds would be my priority, but getting rid of that annoying error message at startup, and not having to type reboot each time would be of some help too...

---

### Post by taurus on 2007-11-24
Can you post

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by Chymera on 2007-11-24
here's the output of the first line 

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004a655

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         249     2000061   82  Linux swap / Solaris
/dev/sda2             250        1708    11719417+  83  Linux
/dev/sda3   *        1709        3288    12691350   83  Linux

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09fa09fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14945   120045681    7  HPFS/NTFS

Disk /dev/sdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd36ab366

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        8174    65657623+   7  HPFS/NTFS

Disk /dev/sdd: 1019 MB, 1019215872 bytes
14 heads, 45 sectors/track, 3159 cylinders
Units = cylinders of 630 * 512 = 322560 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        3160      995203+   b  W95 FAT32

Disk /dev/sdh: 4125 MB, 4125622272 bytes
255 heads, 63 sectors/track, 501 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x449015bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1         501     4024251    b  W95 FAT32

Disk /dev/sdi: 1 MB, 1474560 bytes
1 heads, 3 sectors/track, 960 cylinders
Units = cylinders of 3 * 512 = 1536 bytes
Disk identifier: 0x69737369

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1   ?   623257122   679486963    84344761   69  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(68, 13, 10) logical=(623257121, 0, 3)
Partition 1 has different physical/logical endings:
     phys=(288, 115, 43) logical=(679486962, 0, 1)
Partition 1 does not end on cylinder boundary.
/dev/sdi2   ?   567173161  1190466982   934940732+  73  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(371, 114, 37) logical=(567173160, 0, 2)
Partition 2 has different physical/logical endings:
     phys=(366, 32, 33) logical=(1190466981, 0, 3)
Partition 2 does not end on cylinder boundary.
/dev/sdi3   ?         858         858           0   74  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(371, 114, 37) logical=(857, 0, 3)
Partition 3 has different physical/logical endings:
     phys=(372, 97, 50) logical=(857, 0, 2)
Partition 3 does not end on cylinder boundary.
/dev/sdi4               1  1145037824  1717556736    0  Empty
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 0) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(1145037823, 0, 3)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by Chymera on 2007-11-24
and here' the output of the second one

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=697eefc4-dbe3-45bd-ab0b-5312e34efaff /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=6fc6e40e-f524-4c6a-a83a-200d01059e04 /media/sda2     ext3    defaults        0       2
# /dev/sdb1
UUID=82581E1E581E1191 /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdc1
UUID=4A44AD6444AD540B /media/sdc1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdc3
UUID=660aad53-c2c4-42ad-be3f-d8c23111c3e2 /media/sdc3     ext3    defaults        0       2
# /dev/sda1
UUID=97933144-04c2-4ebe-bc94-6df756cb06a2 none            swap    sw              0       0
# /dev/sdc2
UUID=e136e130-3c71-4f9d-8551-41e9850639ad none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by taurus on 2007-11-24
What about your /boot/grub/menu.lst?

```
cat /boot/grub/menu.lst
```

---

### Post by Chymera on 2007-11-25
Here it is:

> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=697eefc4-dbe3-45bd-ab0b-5312e34efaff ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=697eefc4-dbe3-45bd-ab0b-5312e34efaff ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=697eefc4-dbe3-45bd-ab0b-5312e34efaff ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title           Ubuntu 7.10, kernel 2.6.22-14-rt (on /dev/sda2)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-rt root=UUID=6fc6e40e-f524-4c6a-a83a-200d01059e04 ro quiet splash 
initrd          /boot/initrd.img-2.6.22-14-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title           Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode) (on /dev/sda2)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-rt root=UUID=6fc6e40e-f524-4c6a-a83a-200d01059e04 ro single 
initrd          /boot/initrd.img-2.6.22-14-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title           Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda2)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=6fc6e40e-f524-4c6a-a83a-200d01059e04 ro quiet splash 
initrd          /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda2)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=6fc6e40e-f524-4c6a-a83a-200d01059e04 ro single 
initrd          /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title           Ubuntu 7.10, kernel 2.6.20-16-generic (on /dev/sda2)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=6fc6e40e-f524-4c6a-a83a-200d01059e04 ro quiet splash 
initrd          /boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title           Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode) (on /dev/sda2)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=6fc6e40e-f524-4c6a-a83a-200d01059e04 ro single 
initrd          /boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title           Ubuntu 7.10, memtest86+ (on /dev/sda2)
root            (hd0,1)
kernel          /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc3.
title           Ubuntu, kernel 2.6.20-16-generic (on /dev/sdc3)
root            (hd2,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=660aad53-c2c4-42ad-be3f-d8c23111c3e2 ro quiet splash 
initrd          /boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc3.
title           Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/sdc3)
root            (hd2,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=660aad53-c2c4-42ad-be3f-d8c23111c3e2 ro single 
initrd          /boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc3.
title           Ubuntu, kernel 2.6.20-15-generic (on /dev/sdc3)
root            (hd2,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=660aad53-c2c4-42ad-be3f-d8c23111c3e2 ro quiet splash 
initrd          /boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc3.
title           Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/sdc3)
root            (hd2,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=660aad53-c2c4-42ad-be3f-d8c23111c3e2 ro single 
initrd          /boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc3.
title           Ubuntu, memtest86+ (on /dev/sdc3)
root            (hd2,2)
kernel          /boot/memtest86+.bin  
savedefault
boot


---

### Post by Chymera on 2007-11-25
anyone?

---

### Post by Chymera on 2007-11-25
bump

---

### Post by taurus on 2007-11-27
Which kernel are you booting because I see a bunch of entries in /boot/grub/menu.lst and some of them don't even exist!  There is no /dev/sdc2 (swap) or /dev/sdc3.  Maybe you need to edit your /etc/fstab and comment out those two entries, /dev/sdc2 & /dev/sdc3, then.

---

### Post by fonsi2099 on 2007-11-27
and hier is my case after deletind hte  #s  and UDDs: 

up to now no solution

thanks for post

:-?t :confused:

fdisk -l
Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x247b247a

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2180    17510818+  83  Linux
/dev/hda2            2181        2545     2931862+  83  Linux
/dev/hda3   *        2546        9358    54725422+   7  HPFS/NTFS

Disk /dev/sda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04710470

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1       14596   117242338+   f  W95 Ext'd (LBA)
/dev/sda5            5100        6315     9767488+   b  W95 FAT32
/dev/sda6            7650       10199    20482843+   b  W95 FAT32
/dev/sda7           10200       12749    20482843+   b  W95 FAT32
/dev/sda8           12750       14138    11157111    b  W95 FAT32
/dev/sda9            6316        7649    10715323+  83  Linux
/dev/sda10              1        1216     9767425+  83  Linux
/dev/sda11           1217        1581     2931831   82  Linux swap / Solaris
/dev/sda12           1582        3405    14651248+  83  Linux
/dev/sda13           3406        5099    13607023+   b  W95 FAT32
/dev/sda14          14139       14596     3678853+  83  Linux

Partition table entries are not in disk order

-desktop:~$ cat /etc/fstab

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
/dev/sda10 / reiserfs notail 0 1
/dev/sda12 /home ext3 defaults 0 2
/dev/hda1 /media/hda1 reiserfs defaults 0 2
/dev/hda2 /media/hda2 ext3 defaults 0 2
/dev/hda3 /media/hda3 ntfs-3g defaults,locale=en_US.UTF-8 0 1
/dev/sda13 /media/sda13 ext3 defaults 0 2
/dev/sda5 /media/sda5 vfat defaults,utf8,umask=007,gid=46 0 1
/dev/sda6 /media/sda6 vfat defaults,utf8,umask=007,gid=46 0 1
/dev/sda7 /media/sda7 vfat defaults,utf8,umask=007,gid=46 0 1
/dev/sda8 /media/sda8 vfat defaults,utf8,umask=007,gid=46 0 1
/dev/sda9 /media/sda9 ext3 defaults 0 2
/dev/sda14 /usr/local ext3 defaults 0 2
/dev/sda11 none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0

desktop:~$ cat /boot/grub/menu.lst

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=d706b7aa-165f-44b9-bc48-404c44cc3731 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,9)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,9)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=d706b7aa-165f-44b9-bc48-404c44cc3731 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,9)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=d706b7aa-165f-44b9-bc48-404c44cc3731 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,9)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title           Ubuntu 7.10, kernel 2.6.22-13-generic (on /dev/hda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-13-generic root=UUID=d2066e85-8a93-452f-b168-ca120733a9ac ro quiet splash 
initrd          /boot/initrd.img-2.6.22-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title           Ubuntu 7.10, kernel 2.6.22-13-generic (recovery mode) (on /dev/hda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-13-generic root=UUID=d2066e85-8a93-452f-b168-ca120733a9ac ro single 
initrd          /boot/initrd.img-2.6.22-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title           Ubuntu 7.10, memtest86+ (on /dev/hda1)
root            (hd0,0)
kernel          /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda3
title           Microsoft Windows XP Professional
root            (hd0,2)
savedefault
makeactive
chainloader     +1

---

### Post by Chymera on 2007-12-01
Thank you for your suggestions, I deleted the last entry from my sdc in fstab, and everything is working as well as before.

---

