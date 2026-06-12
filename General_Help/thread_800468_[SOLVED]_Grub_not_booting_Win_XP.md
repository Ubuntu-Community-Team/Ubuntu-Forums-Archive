---
title: "[SOLVED] Grub not booting Win XP"
date: 2008-05-19
forum: General Help
---

### Post by not_surt on 2008-05-19
When trying to boot into my Win XP partition from grub it shows the "Starting up ..." message but then just stops with a blinking cursor.

Any ideas why it won't boot?

Partition is on a SATA disk, with SATA port set in AHCI mode.

I'm sure the partition is correct (sdc3, hd2,2).

Prior to reinstalling grub to MBR the Win install booted fine.

"fdisk -l":```
Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8e34045a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       91201   732572001    7  HPFS/NTFS

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8e6f65b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       91201   732572001    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ad20ad1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         246     1975963+  82  Linux swap / Solaris
/dev/sdc2             247       15935   126021892+  83  Linux
/dev/sdc3   *       15936       30401   116198145    7  HPFS/NTFS
```
/boot/grub/menu.lst:```
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
# kopt=root=UUID=8708c128-fcd4-468b-9da0-9d3f712ea796 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,1)

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
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8708c128-fcd4-468b-9da0-9d3f712ea796 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8708c128-fcd4-468b-9da0-9d3f712ea796 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd2,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc3
title		Windows NT/2000/XP (loader)
root		(hd2,2)
savedefault
chainloader	+1
```

---

### Post by meierfra. on 2008-05-19
Try 

title		Windows NT/2000/XP (loader)
root		(hd2,2)
map             (hd0) (hd2)
map             (hd2) (hd0)
savedefault
chainloader	+1

---

### Post by not_surt on 2008-05-20
> **meierfra. said:**
> Try 

title		Windows NT/2000/XP (loader)
root		(hd2,2)
map             (hd0) (hd2)
map             (hd2) (hd0)
savedefault
chainloader	+1
That didn't solve the problem, but it did lead me to the solution, thanks.

After remapping the drives trying to boot the windows partition brought up the "NTLDR is missing" message, so after a bit of research it was revealed that Windows, naturally, doesn't install it's loader to the partition it is installed on, but to partion zero, of disk zero.

So I just removed the map commands and set root to (hd0,0) and now all works fine.

---

### Post by meierfra. on 2008-05-20
> o I just removed the map commands and set root to (hd0,0) and now all works fine. 

That would have been my next suggestion.:)

---

