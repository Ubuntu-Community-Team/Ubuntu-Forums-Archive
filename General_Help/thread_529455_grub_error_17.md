---
title: "grub error 17"
date: 2007-08-19
forum: General Help
---

### Post by imbjr on 2007-08-19
I have shrunk my XP partition down to 10Gb, ready for attempting to virtualise it, but upon rebooting, I get grub's error 17.

Looking at various pieces of information suggest something is wrong, but I can't put my finger on it:

========================================================
/boot/grub/device/map:

(hd0)	/dev/sda
(hd1)	/dev/sdb

========================================================
/boot/grub/menu.lst:

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
# kopt=root=UUID=6d499680-4a7a-4d97-a937-7a6f1105fe04 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=6d499680-4a7a-4d97-a937-7a6f1105fe04 ro quiet splash
#kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=6d499680-4a7a-4d97-a937-7a6f1105fe04 ro
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=6d499680-4a7a-4d97-a937-7a6f1105fe04 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=6d499680-4a7a-4d97-a937-7a6f1105fe04 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=6d499680-4a7a-4d97-a937-7a6f1105fe04 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Windows NT/2000/XP
root		(hd0,3)
savedefault
makeactive
chainloader	+1

========================================================
/etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=6d499680-4a7a-4d97-a937-7a6f1105fe04 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
#UUID=07D6-0B08  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
#/dev/sda1  /media/sda1     vfat    noauto,ro,utf8,umask=007,gid=46 0       1
# /dev/sda2
#/dev/sda2 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
#/dev/sda4       /media/sda4     vfat    defaults,utf8,umask=007,gid=46 0       1
#/dev/sda4       /media/sda4     vfat    noauto,ro,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=86A1-98FC  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda7
/dev/sda7 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
#usbfs
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

========================================================

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8        1313    10485760+   7  HPFS/NTFS
/dev/sda3           16979       38307   171325192+   5  Extended
/dev/sda4           38308       38913     4867695   db  CP/M / CTOS / ...
/dev/sda5           16979       33630   133757127   83  Linux
/dev/sda6           33631       34129     4008186   82  Linux swap / Solaris
/dev/sda7           34131       38307    33551752+   b  W95 FAT32

========================================================

From menu.lst,
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,5)

this seems wrong as /dev/sda5 has linux on it - shouldn't that be (hd0,6) - though I've tried that and it did not work.

I also tried commenting out menu.lst's references to XP.

I also tried making the ext3 partition directly bootable instead of the NTFS one.

I noticed that after shrinking the NTFS partition, my sdN references seemed different. I could have sworn that /dev/sda7 used to be /dev/sda5 for the 32Gb FAT32 partition. 

Plus: fstab is now pointing at the wrong swap location. Maybe I should use an UUID for that but I don't know how to look that up. But that's an fstab problem not a grub problem(?)

I'm stumped.

---

### Post by imbjr on 2007-08-19
As suspected, grub was indeed pointing at the wrong places - and my fix was also pointing at the wrong places. Eventually I got the right hd0 references.

---

### Post by confused57 on 2007-08-19
Good job finding the solution...here's how to determine the current UUID's of your filesystems:
[http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with](http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with)

---

