---
title: "Cannot Startup Vista after Installing Ubuntu 7.10"
date: 2007-11-23
forum: General Help
---

### Post by arthrane on 2007-11-23
There seem to be aplenty of related threads, but none have helped. I'm usually not much of a geeky person, so excuse my muddled thoughts. :confused:

I installed from the live CD, and followed the defaults. When I start-up, I get the GRUB with Ubuntu, Ubuntu (recovery), Ubuntu memtest, and Windows Vista/Longhorn (loader). Ubuntu works like a gem, but if I try to run Windows Vista it goes into recovery mode. When it asks which OS to repair, Vista doesn't show up.

If I go to Computer, I see multiple partitions (or at least, I think I do!). One of them is in essence the C: drive, and old files still show up. Another one is Filesystems, and it seems to hold the things for Ubuntu.

One of the friends I asked for help (but we are still unable to resolve the problem) told me to copy these in, so here it is:

arthrane@arthrane-laptop:~$ sudo fdisk -l
[sudo] password for arthrane:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe0779162

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        7037    54982422    7  HPFS/NTFS
/dev/sda3            7038        9611    20675655   83  Linux
/dev/sda4            9612        9729      947835    5  Extended
/dev/sda5            9612        9729      947803+  82  Linux swap / Solaris
arthrane@arthrane-laptop:~$ 
arthrane@arthrane-laptop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=e8bd62f3-d83c-4f79-9c9c-292c91ba29cb ro

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
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=e8bd62f3-d83c-4f79-9c9c-292c91ba29cb ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=e8bd62f3-d83c-4f79-9c9c-292c91ba29cb ro single
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista/Longhorn (loader)
root            (hd0,1)
savedefault
makeactive
chainloader     +1

arthrane@arthrane-laptop:~$ uname -a
Linux arthrane-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

As a last sidenote, I do not have the CDs for XP or Vista with me, although I suppose I'll have to scrap them up if absolutely necessary.

Any help would be enormously appreciated! :)

---

### Post by OliW on 2007-11-23
Here's the really hacky-way I fixed mine when I first started out with grub. Sorry I don't have a more scientific way of doing this.

Restart and when you get to grub, press escape to enter the menu. Scroll down to your windows entry and press "e" to edit it. Find the list entry with the "hd0,1" line on it, and try changing the second number. (eg to: "hd0,0" or "hd0,2").

There's another key you need to press to boot (I can't remember off the top of my head but it lists the options at the bottom of the screen). If one works, write down what it is, shut down Windows (important if you want to use that partition from inside Linux too), go back into Linux-land and edit that number back into the "title Windows Vista/Longhorn (loader)" section of the /boot/grub/menu.lst

---

### Post by arthrane on 2007-11-23
After doing that, I get "BOOTMGR is missing", Ctrl-Alt-Del to restart.

:confused:

---

### Post by arthrane on 2007-11-25
It's fixed!

[http://ubuntuforums.org/showthread.php?t=620836](http://ubuntuforums.org/showthread.php?t=620836) if you would like to see what I did.

Thank you everyone! :KS

---

