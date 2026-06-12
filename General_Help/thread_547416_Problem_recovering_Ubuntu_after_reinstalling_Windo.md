---
title: "Problem recovering Ubuntu after reinstalling Windows"
date: 2007-09-10
forum: General Help
---

### Post by nemarona on 2007-09-10
I have a computer with two hard drives, one for WinXP (/dev/hda) and one for Ubuntu (/dev/hdb). I recently had to reinstall Windows, and knew I had to follow the instructions in

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) (RUAIW)

to "recover" Ubuntu, i.e. to again have Grub popup at boot time and ask me to choose an OS.

My problem is, I've tried every option given in RUAIW, but nothing seems to work. Here's a description of everything I've tried:

1) Boot the Kubuntu 7.04 Live CD and open a terminal (Konsole)
2) fdisk -l gives

```
Disk /dev/hda: 20.0 GB, 20000000000 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2430    19518943+   c  W95 FAT32 (LBA)

Disk /dev/hdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9918    79666303+  83  Linux
/dev/hdb2            9919       10011      747022+   5  Extended
/dev/hdb5            9919       10011      746991   82  Linux swap / Solaris
```

Is it ok to have two bootable partitions (they're on different HDs)?

3) Grub is installed, and when I run it and type "find /boot/grub/stage1" I get "(hd1,0)", which corresponds, I believe, to hdb1.

4) If I tell BIOS to boot from the first HD (/dev/hda) then there's no trace of Grub and Windows starts.

5) If I tell BIOS to boot from the second HD (/dev/hdb) then Grub shows up, but
5a) if I choose Kubuntu, I get an "Error 15: File not found", and
5b) if I choose Windows, then Grub shows up again and I can't get past there.

I've tried all combinations of making /dev/hda1 and/or /dev/hdb1 bootable, but none seem to work.

I'm surely doing something wrong here, but can't figure out what. Any help would be greatly appreciated!

---

### Post by McNils on 2007-09-10
> 3) Grub is installed, and when I run it and type "find /boot/grub/stage1" I get "(hd1,0)", which corresponds, I believe, to hdb1.
To be sure look in /boot/grub/device.map. This file maps the drive to the grub name. It sounds like the mapping is wrong.

---

### Post by merlinus on 2007-09-10
Maybe this will help:

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by vanadium on 2007-09-10
It is indeed the mapping. grub uses its own naming sheme. In good C tradition, grub starts to count with 0. My first (and only) drive is hd0. Your first partition on your second drive will probably be hd1,0 for grub.

---

### Post by nemarona on 2007-09-10
Hi and thanks for all replies. I'm on my way to work, so I'll just post my /boot/grub/device.map and try all other suggestions as soon as I come back home:
```
(hd0)   /dev/hda
(hd1)   /dev/hdb
```
This looks ok to me...

---

### Post by nemarona on 2007-09-10
Here's my /boot/grub/menu.lst (I thought it could be important):
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
# kopt=root=UUID=9687bb28-eef5-4e1e-ba10-e87351aced5d ro

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
# defoptions=quiet splash locale=es_ES

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
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=9687bb28-eef5-4e1e-ba10-e87351aced5d ro quiet splash locale=es_ES
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=9687bb28-eef5-4e1e-ba10-e87351aced5d ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=9687bb28-eef5-4e1e-ba10-e87351aced5d ro quiet splash locale=es_ES
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=9687bb28-eef5-4e1e-ba10-e87351aced5d ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by logos34 on 2007-09-10
> **nemarona said:**
> 3) Grub is installed, and when I run it and type "find /boot/grub/stage1" I get "(hd1,0)", which corresponds, I believe, to hdb1.

4) If I tell BIOS to boot from the first HD (/dev/hda) then there's no trace of Grub and Windows starts.


Not sure what exactly what happened here.  Maybe you reinstalled grub to (hd1,0) or something.

With the Bios set to boot the windows drive (hda) first, try reinstalling grub once more like this:

> sudo grub
root (hd1,0)
setup **(hd0)**
quit

---

### Post by nemarona on 2007-09-10
logos34's suggestion just did the trick :D

I had been previously installing grub to the root partition, (hd1,0) = hdb1. When I switched to installing grub to the first HD, hd0, and configured BIOS to boot from that HD, everything went fine.

I also changed some suspicious lines on my menu.lst; the ones that read
```
kernel		/boot/vmlinuz-2.6.20-16-generic **root=UUID=9687bb28-eef5-4e1e-ba10-e87351aced5d** ro quiet splash locale=es_ES
```
I changed to
```
kernel		/boot/vmlinuz-2.6.20-16-generic **root=/dev/hdb1** ro quiet splash locale=es_ES
```
No idea as to whether this amounted to something or not.

I'm very thankful to all who replied and helped me solved this!

If anyone could comment, however, on *why* this had to be configured like this to work, I would also appreciate it.

---

