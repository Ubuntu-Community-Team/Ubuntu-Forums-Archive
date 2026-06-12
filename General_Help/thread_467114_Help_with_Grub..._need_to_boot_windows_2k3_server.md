---
title: "Help with Grub... need to boot windows 2k3 server"
date: 2007-06-07
forum: General Help
---

### Post by screechingcat on 2007-06-07
i had windows vista and windows server 2003 installed on an 80gig and 160gig hard disk respectively. yesterday the 80gig hd died. so i removed it. i partitioned the 160gig hd into 100gb and 60gb and installed ubuntu on the 60gig partition. i still have windows server 2k3 on the 100gb partition. when i installed ubuntu, it detected a vista/longhorn bootloader and added it to grub. but when the hard disk died, the vista bootloader seems to have become corrupt. i need to boot into the server. can someone tell me what lines i need to add to my menu.lst ?

this is my etc/fstab - 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=53fb4ed8-a63f-4f08-97ab-a85f06c29744 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=B2B4D1BAB4D180F1 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=dba5344f-c014-428a-bc9b-152ae37d1332 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

---

### Post by confused57 on 2007-06-07
There's an example in your menu.lst that may work:
```
title		Windows 95/98/NT/2000
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

If it doesn't, you might want post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

and
```
gedit /boot/grub/menu.lst
```

---

### Post by screechingcat on 2007-06-07
here's the fdisk output - 

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12748   102398278+   7  HPFS/NTFS
/dev/sda2   *       12749       18827    48829567+  83  Linux
/dev/sda3           18828       19457     5060475   82  Linux swap / Solaris

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       60801   488384001    7  HPFS/NTFS

```

and this is my menu.lst

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

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
# kopt=root=UUID=53fb4ed8-a63f-4f08-97ab-a85f06c29744 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=53fb4ed8-a63f-4f08-97ab-a85f06c29744 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=53fb4ed8-a63f-4f08-97ab-a85f06c29744 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=53fb4ed8-a63f-4f08-97ab-a85f06c29744 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=53fb4ed8-a63f-4f08-97ab-a85f06c29744 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader) 
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by confused57 on 2007-06-07
I don't have Vista, so I'm not familiar with how the Vista bootloader works...I'm assuming Vista added an entry to the Window's 2000 boot.ini file(this would be the case for XP, Win2000?).  You would probably need to boot a Windows 2000 install cd, enter recovery console by pressing "r", then enter FIXMBR & FIXBOOT.

[http://www.winmatrix.com/forums/index.php?showtopic=6844](http://www.winmatrix.com/forums/index.php?showtopic=6844)

Hopefully, someone familiar with Vista's bootloader can offer you more specific advice.

Added:  Did your Win2000 boot OK after you removed your Vista drive & repartitioned the 160 Gb drive, but before you installed Ubuntu?

You can reinstall grub with the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by screechingcat on 2007-06-08
no it didnt start after i installed ubuntu. i think the bootsector got corrupted when the lod hard disk failed. i thought installing ubuntu might fix the problems as it overwrites the mbr. but it has preserved the vista bootloader.

---

### Post by confused57 on 2007-06-08
> **screechingcat said:**
> no it didnt start after i installed ubuntu. i think the bootsector got corrupted when the lod hard disk failed. i thought installing ubuntu might fix the problems as it overwrites the mbr. but it has preserved the vista bootloader.

If you have a Window's 2000 install cd, you could probably run "fixboot" to repair the bootloader.

---

