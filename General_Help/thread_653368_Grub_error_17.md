---
title: "Grub error 17"
date: 2007-12-29
forum: General Help
---

### Post by Jedi007 on 2007-12-29
"Cannot mount partition"

This error is really weird though. I installed ubuntu on my USB and it consequently installed grub in the mbr of my main harddrive (which I obviously don't want), and it booted fine. So then I installed grub on my usb with linux and restarted my computer, selected ubuntu and I got this error... So I was like okay I probably screwed my ubuntu up! The weird thing is I didn't. I restarted my PC and this time I booted from my harddrive and I selected ubuntu and it worked (?!). 

I thought the boot partition command thingy (don't know what it's called) must be messed up, so I copied down the "root", "kernel", "initrd" and quiet values to a piece of paper and compared them to the values on my USB grub. To my surprise they were identical! I am super confused now, the only thing that I can think of is because it's booting off the USB the root could be hd0,0, but I tried and got the same error..?

Any help will be greatly appreciated!!

Here is some info :

sudo fdisk -l
(sda = data (i think grub is on it), sdb = windows vista, sdc = memory   stick with ubuntu)

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c51c5b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       19457   156280320    f  W95 Ext'd (LBA)
/dev/sda5               2       19457   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08c78f00

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9730    78148608    7  HPFS/NTFS

Disk /dev/sdc: 4083 MB, 4083154944 bytes
126 heads, 62 sectors/track, 1020 cylinders
Units = cylinders of 7812 * 512 = 3999744 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         769     3003683   83  Linux
/dev/sdc2             770        1020      980406   82  Linux swap / Solaris

```

menu.1st
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
# kopt=root=UUID=200f9708-cecb-4875-bb7c-c1a20192207f ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=200f9708-cecb-4875-bb7c-c1a20192207f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=200f9708-cecb-4875-bb7c-c1a20192207f ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

please respond if you have any suggestions or anything! thanks!

---

### Post by logos34 on 2007-12-29
> **Jedi007 said:**
>  the only thing that I can think of is because it's booting off the USB the root could be hd0,0, but I tried and got the same error..

yep, should be (hd0,0)...Make sure the Bios hard disk boot priority is set to boot the USB drive first.

---

### Post by smartboyathome on 2007-12-29
I had this same problem with Arch (actually you just solved the problem for me). You have to take out the internal hard drive and then install Ubuntu. Then it will be in the right place.

---

### Post by meierfra on 2007-12-29
I wrote a howto for this situation. Click on DualTwo in my signature.

---

### Post by Jedi007 on 2007-12-29
thank you so much, logos34 and all you other guys for suggestions! it works :)

---

