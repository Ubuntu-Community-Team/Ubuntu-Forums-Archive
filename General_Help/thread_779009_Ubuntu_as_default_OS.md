---
title: "Ubuntu as default OS"
date: 2008-05-02
forum: General Help
---

### Post by albymilan on 2008-05-02
Hi everyone, I have the new Ubuntu version from 2 days.
At the boot I have 2 options: Windows XP and Ubuntu.
I want to set Ubuntu as default OS, so I searched in the net and I found this solution: open /boot/grub/menu.lst and change the number after the word "default" to 0
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
**default		0**
```

But I noticed that this number was already 0.
I also read something about the order of the lines like these:
```
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
chainloader	+1
```
but in my menu.lst , at the end, there are before the lines concerning Ubuntu. (3 paragraphs)

So I've understanded that maybe the choice that I have at the boot is not the grub.
I think this because if I select Ubuntu, it appears ```
press ESC for the menu
``` and a countdown. If I press ESC I can see the 4 choices that i saw in the /boot/grub/menu.lst

So I ask you: how can I change the order of OS at the boot? Have I to do this from Windows?

Thanks for the replies and sorry for my english.

---

### Post by GavinZac on 2008-05-02
Does the screen where you choose Windows or Linux look like this?:

[img]http://static.flickr.com/61/158560702_d11b6e3889_o.jpg[/img]

---

### Post by albymilan on 2008-05-02
> **GavinZac said:**
> Does the screen where you choose Windows or Linux look like this?:

[img]http://static.flickr.com/61/158560702_d11b6e3889_o.jpg[/img]

No, that's in fact the problem.
This screen appears me when I select Ubuntu and I press ESC.

First I have only two choices: Windows XP etc...and Ubuntu.

---

### Post by TeoBigusGeekus on 2008-05-02
Post us your whole menu.lst file please.

---

### Post by albymilan on 2008-05-02
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
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#

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
# kopt=root=UUID=A871-0DD6 loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)/ubuntu/disks

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
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=A871-0DD6 loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=A871-0DD6 loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
chainloader	+1

```

---

### Post by TeoBigusGeekus on 2008-05-02
Open a terminal and type
```
sudo fdisk -l
```
that's -L
and post us the results.

---

### Post by jimv on 2008-05-02
"(hd0,0)/ubuntu/disks"


Is this a wubi install?

Because here's a snippet from the wubi guide:

> How do I make Ubuntu the default boot option?

Ubuntu is not installed as the default boot option, you have to select it in the windows boot menu. To change that, in windows XP go to control_panel > system > advanced > startup_and_recovery and edit the "Default Operating System", if you want you can change the timeout as well. 

---

### Post by albymilan on 2008-05-02
> **TeoBigusGeekus said:**
> Open a terminal and type
```
sudo fdisk -l
```
that's -L
and post us the results.
It's in Italian.
```
Disco /dev/sda: 60.0 GB, 60022480896 byte
255 heads, 63 sectors/track, 7297 cylinders
Units = cilindri of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8fa28fa2

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7297    58613121    c  W95 FAT32 (LBA)
Nota: la dimensione del settore è 2048 (non 512)

Disco /dev/sdb: 4060 MB, 4060086272 byte
103 heads, 42 sectors/track, 458 cylinders
Units = cilindri of 4326 * 2048 = 8859648 bytes
Disk identifier: 0x20202020

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          12       96264    0  Vuoto
La partizione 1 ha diversi elementi iniziali fisici/logici (non Linux?):
     phys=(0, 1, 1) logico=(0, 1, 22)
La partizione 1 ha diversi elementi finali fisici/logici:
     phys=(2, 254, 63) logico=(11, 14, 21)
La partizione 1 non termina al limite del cilindro.
/dev/sdb2              12         459     3868536    b  W95 FAT32
La partizione 2 ha diversi elementi iniziali fisici/logici (non Linux?):
     phys=(3, 0, 1) logico=(11, 14, 22)
La partizione 2 ha diversi elementi finali fisici/logici:
     phys=(123, 102, 42) logico=(458, 27, 21)

```

Disco=disk
Partizone=partition
ha diversi elementi=has different elements
fisici=physics
logici=logics

---

### Post by albymilan on 2008-05-02
> **jimv said:**
> "(hd0,0)/ubuntu/disks"


Is this a wubi install?

Because here's a snippet from the wubi guide:

Yes, it's a wubi install. Now i try, but I'm sure this is the solution

Big thanks to everyone.

---

### Post by TeoBigusGeekus on 2008-05-02
Ubuntu and window$ on the same partition (hd0,0 -> sda1)? See post above...

---

### Post by albymilan on 2008-05-02
It works. Thanks!

P.s.: LOL windows looks so stupid and obsolete :D

---

