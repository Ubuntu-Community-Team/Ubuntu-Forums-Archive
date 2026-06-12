---
title: "partition problems???"
date: 2007-06-17
forum: General Help
---

### Post by jayslapmc on 2007-06-17
hey
i have a really wierd problem, each time i restart my computer what used to be sda1 is now sdc1 and sdb1 is sda1 and so on and so on. there are 3 hard drives and it seems the uuid(sp?) in fstab is no help whatsoever.

i just dont know what to do apart from a fresh install

---

### Post by confused57 on 2007-06-17
> **jayslapmc said:**
> hey
i have a really wierd problem, each time i restart my computer what used to be sda1 is now sdc1 and sdb1 is sda1 and so on and so on. there are 3 hard drives and it seems the uuid(sp?) in fstab is no help whatsoever.

i just dont know what to do apart from a fresh install
You'll need to provide a little more information...if you can't boot into Ubuntu, from the live cd, open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

You might also want to post your fstab & menu.lst boot entries also:
```
gedit /boot/grub/menu.lst
gedit /etc/fstab
```
if you're using the live cd, you'll need to mount your root partition first:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

You can use "blkid" to determine your current UUID's, which you can compare to the ones in your fstab & menu.lst kernel line root entry...they shouldn't have changed, but won't hurt to check.

---

### Post by joe.turion64x2 on 2007-06-17
Did you open your machine and changed cable's order? That could account for the confusion.

Joe.

---

### Post by jayslapmc on 2007-06-18
sudo fdisk -l gives:

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641   83  Linux

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24041   193109301   83  Linux
/dev/sdb2           24042       24792     6032407+   5  Extended
/dev/sdb5           24042       24792     6032376   82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321    7  HPFS/NTFS

```

boot/grub/menu.lst gives:
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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=fec4b85b-e362-440e-93c3-0b897424b33f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fec4b85b-e362-440e-93c3-0b897424b33f ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fec4b85b-e362-440e-93c3-0b897424b33f ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=fec4b85b-e362-440e-93c3-0b897424b33f ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=fec4b85b-e362-440e-93c3-0b897424b33f ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

and finally /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdc1
UUID=ff14dcac-c545-4e05-aff8-fb0f26b9d78e	/               ext3    defaults 	0       1
/dev/sdc5
UUID=013bacba-9752-4ff4-8db3-e7c42c0a83b8	none            swap    sw              0       0
/dev/sda1
 UUID=fb682f82-d4a8-43ab-809f-82578c23ec16	/media/sda1     ext3    defaults        0       0
/dev/sdb1
 UUID=fec4b85b-e362-440e-93c3-0b897424b33f	/media/Video	ext3	defaults	0	0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


```

hope you can help:) thanks

---

### Post by confused57 on 2007-06-18
A reinstall would probably be easier...but there are several things you could try to get your current install booting.

Open a terminal and run the command:
```
blkid
```

compare the UUID's with the ones that you have in your fstab and the root in your menu.lst kernel line...your current kernel root UUID doesn't match the UUID for your root partition mounted in fstab(the kernel root UUID actually matches the UUID in your sda linux partition).

You can change the /dev/sdx designations in your fstab, just put a # in front of...this is to identify which partition your UUID is for:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#/dev/sdb1
UUID=ff14dcac-c545-4e05-aff8-fb0f26b9d78e	/               ext3    defaults 	0       1
#/dev/sdb5
UUID=013bacba-9752-4ff4-8db3-e7c42c0a83b8	none            swap    sw              0       0
#/dev/sda1<----or if this is your actual sda1(check blkid for which it is)
UUID=fb682f82-d4a8-43ab-809f-82578c23ec16	/media/sda1     ext3    defaults        0       0
#/dev/sda1<----I'm not sure which is your sda1
 UUID=fec4b85b-e362-440e-93c3-0b897424b33f	/media/Video	ext3	defaults	0	0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

I assume your /dev/sdc1 is a Window's install, but I noticed you don't have an entry in your menu.lst?  It's not mounted in fstab?
Your "sudo fdisk -l" should identify your hard drives, then "blkid" will give your the correct UUID's necessary for mountpoints in fstab and root in the menu.lst kernel line.

If you can't boot your Ubuntu install, you can do this using the live cd, but you'll need to mount your root partition first:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

It will require copy & pasting the "blkid" UUID outputs into your fstab & kernel line, but you can give it a go, if you feel it's worth the effort.  No guarantees it'll work, only thing you have to lose is your time.

You might also want to check the output of:
```
gedit /boot/grub/device.map
```
I'm not sure which drive you're booting to first, but evidently your sdb is last in your bios hard drive boot order, by root being (hd2,0).

I probably haven't explained it very well, but I hope you get the gist of what you need to do.

---

