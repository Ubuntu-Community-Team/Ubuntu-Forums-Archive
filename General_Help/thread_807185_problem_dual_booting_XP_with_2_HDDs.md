---
title: "problem dual booting XP with 2 HDDs"
date: 2008-05-25
forum: General Help
---

### Post by NerdHerd628 on 2008-05-25
Hello board.

I am having trouble dual-booting hardy and  windows XP.  I have two Hard drives, a 20GB one and then a 160 GB one.  First I installed Windows XP on the second and larger HD.  Then I installed hardy on the first and smaller HD.  The problem is that when GRUB starts, it doesn't find Windows XP as an option to boot.

Is it possible to fix this without reinstalling windows again?

---

### Post by ibuclaw on 2008-05-25
Yes, luckily it is.

Can you open up a terminal and post the output of this command:
```
cat /boot/grub/menu.lst
```
And we'll guide you through what to add and where.

Regards
Iain

---

### Post by TeoBigusGeekus on 2008-05-25
Post us the output of 
```
sudo fdisk -l
```
(-L)
and the contents of your menu.lst file
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by NerdHerd628 on 2008-05-26
This is the menu.lst contents:

***** cat /boot/grub/menu.lst *************


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
# kopt=root=UUID=b896a485-7e45-4d70-b777-db36336c8879 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b896a485-7e45-4d70-b777-db36336c8879 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b896a485-7e45-4d70-b777-db36336c8879 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by NerdHerd628 on 2008-05-26
This is the fdisk -l

*****************************************************************************
sudo fdisk -l

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd478bc7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2327    18691596   83  Linux
/dev/sda2            2328        2434      859477+   5  Extended
/dev/sda5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dc09c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19456   156280288+   7  HPFS/NTFS



Thanks for replying!

---

### Post by TeoBigusGeekus on 2008-05-26
```
gksudo gedit /boot/grub/menu.lst
```
(.LST)

Add these lines at the end of the file
```
title Gadam Window$ XP
root (hd1,0)
makeactive
chainloader +1
```
save and reboot.

---

### Post by NerdHerd628 on 2008-05-26
It hangs at "Starting up..."

quick question: does the title have to read "Gadam Window$ XP" and does the order matter?

---

### Post by TeoBigusGeekus on 2008-05-26
Make it then 
```
title           Windows XP Professional
root            (hd1,0)
savedefault
makeactive
chainloader     +1
map (hd0) (hd1)
map (hd1) (hd0)
```

The title can be anything you want. Sorry for the gadam thing, bad humor.
The order doesn't matter as well.

Anyway, try it and post us what happened.

---

### Post by NerdHerd628 on 2008-05-26
now it says "NTLDR is missing"

---

### Post by sweeneytodd on 2008-05-26
I think xp has to be on the master hard drive, primary partition,and it looks like u have on your slave.

---

