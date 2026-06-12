---
title: "Dual boot help ~ Xubuntu &amp; XP"
date: 2008-02-23
forum: General Help
---

### Post by StageCraft on 2008-02-23
I have just instaled Xubuntu on my Gateway laptop and now when I try to start Windows all I get is this

Starting up...


And it wont even acces the hard drive.

I still need some programs on that partition. What should I do?

Thanks in advance for any help

---

### Post by mikewhatever on 2008-02-23
Can you post the outputs of the following commands from Xubuntu terminal:
sudo fdisk -l
cat /boot/grub/menu.lst
cat /boot/grub/device.map

---

### Post by StageCraft on 2008-02-23
I'll try but it'll take a while, for some reason I cant find a wifi connnection even tough my nokia 770 can (thats whaat i'm on right now)

---

### Post by StageCraft on 2008-02-23
> **mikewhatever said:**
> Can you post the outputs of the following commands from Xubuntu terminal:
sudo fdisk -l
cat /boot/grub/menu.lst
cat /boot/grub/device.map

here's what I get:

[ > sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *        1061        9729    69633742+   7  HPFS/NTFS
/dev/hda2               1        1021     8201151   83  Linux
/dev/hda3            1022        1060      313267+  82  Linux swap / Solaris

Partition table entries are not in disk order]


> [cat /boot/grub/menu.lst
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
# kopt=root=UUID=457477e4-a978-4d2e-81ae-f28b59927df3 ro

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
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-rt
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-rt root=UUID=457477e4-a978-4d2e-81ae-f28b59927df3 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-rt
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-rt root=UUID=457477e4-a978-4d2e-81ae-f28b59927df3 ro single
initrd          /boot/initrd.img-2.6.22-14-rt

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=457477e4-a978-4d2e-81ae-f28b59927df3 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=457477e4-a978-4d2e-81ae-f28b59927df3 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1]

> [cat /boot/grub/device.map
(hd0)   /dev/hda]

---

### Post by HoLLyw00dGT on 2008-02-26
I have the same problem...FINALLY got grub to show linux and my xp....tried xp and all i got was

Starting...

Tried linux, i'm on it right now. 

-Justin

---

### Post by StageCraft on 2008-02-26
I think the problem may be that Windows doesn't like being on the second partition ( and I think thats where it is )  but I have no idea how to fix that. I love Xubuntu and will keep using it but I would still love to have the option of using some of my old programs.

---

### Post by torgrot on 2008-02-26
Your Windows is on your first partition not the second.  You could try rootnoverify like this:

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Home Edition
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

```

But I really don't see anything wrong.

torgrot

---

### Post by StageCraft on 2008-02-28
How would I change that and what would it do?

---

