---
title: "weird Grub menu question"
date: 2008-05-08
forum: General Help
---

### Post by jjascarm on 2008-05-08
I have recently installed Ubuntu 8.04 in a dual boot system.
I have three hard drives two 320GB SATA drives and one 80GB IDE drive. The SATA drive with Ubuntu (and Grub) installed on it is set as the first drive in the bios, and the IDE drive has Windows XP on it is set as the third drive. 
I can boot Ubuntu, but not XP. My fdisk output is as follows:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes

255 heads, 63 sectors/track, 9729 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0xebb6ebb6

Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes

255 heads, 63 sectors/track, 38913 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0xae801b68

Device Boot      Start         End      Blocks   Id  System

/dev/sdb1   *           1       37967   304969896   83  Linux

/dev/sdb2           37968       38913     7598745    5  Extended

/dev/sdb5           37968       38913     7598713+  82  Linux swap / Solaris

Disk /dev/sdc: 320.0 GB, 320072933376 bytes

255 heads, 63 sectors/track, 38913 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x0008e53c

Device Boot      Start         End      Blocks   Id  System

/dev/sdc1               1       38913   312568641    7  HPFS/NTFS


``` 
From this it looks like the Windows XP disk should be HD0,0 and the Ubuntu disk HD1,0 in the Grub menu.lst file but Ubuntu will not boot if it  is set to HD1,0 (it is set to HD0,0)I have also tried HD1,0 and HD2,0 for the XP disk and neither seems to work. I get a "unrecognised device name" error when I try to load windows.

Any help would be appreciated

---

### Post by didac on 2008-05-08
It's not that weird :)

Can you post your /boot/grub/menu.lst ?

Also post your boot.ini if you can access your windows partition. It's in the root directory. Should be in /media/sdc1

---

### Post by lewis1711 on 2008-05-08
Grub probably thinks windows should be on your second hd, not your third. Post your menu.lst as didac said and it should become pretty clear.

---

### Post by jjascarm on 2008-05-08
Thanks guys here is my menu.lst file:
```
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
default		4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=2dddc697-cb07-4ebb-9ea1-62d11ef85a4b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2dddc697-cb07-4ebb-9ea1-62d11ef85a4b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2dddc697-cb07-4ebb-9ea1-62d11ef85a4b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
map		(hd0)(hd2)
map 		(hd2)(hd0)
root		(hd2,0)
savedefault
chainloader	+1
makeactive

```

and here is the boot.ini file:
```
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
```

Thanks for your help

---

### Post by didac on 2008-05-08
Windows loader thinks Xp is in the first hard disk. Grub is trying to 'cheat' Windows into making it think that is so. Grub does it with the lines

```
map		(hd0)(hd2)
map 		(hd2)(hd0)
```

Somehow it doesn't succeed, I don't know why.

Why don't you try playing around with boot.ini ? The line

```
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
```

can be changed to

```
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition 1st disk 2nd partition"
```

or to 

```
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Home Edition 2nd disk 1st partition"
multi(0)disk(0)rdisk(2)partition(1)\WINDOWS="Microsoft Windows XP Home Edition 3rd disk 1st partition"
```


And try, and try until you get it. I don't understand why it's happening. If you get too tired, get instructions on how to boot linux from windows bootloader. But you have to know very well what you are doing. You may get Linux cut off.

Sorry, I'm leaving for the weekend. Hope it helps.

---

### Post by didac on 2008-05-08
Sorry, jjascarm. I'm misleading you. You said:

> I have three hard drives two 320GB SATA drives and one 80GB IDE drive. The SATA drive with Ubuntu (and Grub) installed on it is set as the first drive in the bios, and the IDE drive has Windows XP on it is set as the third drive.


Is Xp in your first hard disk or in the third? Looking at the output from fdisk, sda1 is bootable, while sdc2 is not. Therefore it seems XP is in the first hard disk, sda, while Ubuntu is in the second, sdb. Then, your menu.lst entry for XP should read:

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
chainloader	+1
makeactive

```

The Debian installer found XP in sda1. Try it now.

Also, you can boot with grub and start a command, typing the grub commands from there and testing till you get it.

Now I'm really leaving, well in 2 hours time.

---

