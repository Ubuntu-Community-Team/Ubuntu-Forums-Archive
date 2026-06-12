---
title: "GRUB and Default Windows Boot Loader"
date: 2008-04-04
forum: General Help
---

### Post by Josellis on 2008-04-04
Before I installed Ubuntu, I already had two hard drives (both Windows XP SP2), and the default windows boot loader (NTLDR) would come up and ask me which one I wanted,

To install ubuntu, I partitioned my second hard drive (there was plenty of space I didn't use).

The problem is, GRUB will give me the normal Ubuntu options (Ubuntu, recovery mode and memtest) and at the bottom of the list is the Windows loader, which brings me to NTLDR, and I then have to select an option there.

Is there a way to configure GRUB to include both Windows installs into the list or will I have to go through two boot loaders each time I load Windows?

---

### Post by amlucent23 on 2008-04-04
yes you can defiantly do it. you just have to make a new entry in grub and specify where (which hard drive and partition) it is located.

---

### Post by Josellis on 2008-04-04
ok, good news

now, how do I do that?

I know which drives, but how do I know which partition?

and when I find out, how do I put it in grub? do I add an entry in menu.lst? or do I load GRUB and then use extra options?

---

### Post by Josellis on 2008-04-04
ok, this might help a little

the menu.lst file:
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
timeout		5

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
# kopt=root=UUID=d59b14b4-f865-4210-9446-3b9a0c90be11 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title		Ubuntu 7.10
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d59b14b4-f865-4210-9446-3b9a0c90be11 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d59b14b4-f865-4210-9446-3b9a0c90be11 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10 memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

and the boot.ini used by NTLDR
```
[boot loader]

timeout=10

default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

```

What do I have to add in the menu.lst in order to have the option of loading Windows directly from GRUB without the NTLDR?

and btw, I tried adding ```
# Windows XP SP2 on C Drive
title		Windows XP SP2 on C Drive
root		(hd0,1)
savedefault
makeactive
chainloader	+1

# Windows XP Sp2 on D Drive
title		Windows XP SP2 on D Drive
root		(hd1,1)
savedefault
makeactive
chainloader	+1
```

but it didn't do work

---

### Post by amlucent23 on 2008-04-05
At first glance I see a problem

I am pretty sure you cant have them both default.  The first hard disk is hd0 to grub, the first partition is also numbered as 0 to grub, so I adjusted your info below assuming...  Try this 

```
# Windows XP SP2 on C Drive
title		Windows XP SP2 on C Drive
root		(hd0,0)
savedefault
makeactive
chainloader	+1

# Windows XP Sp2 on D Drive
title		Windows XP SP2 on D Drive
root		(hd1,0)
makeactive
chainloader	+1
```

also I dont know if they both need the "make active" switch

can you get into the first xp partition? the one that ubuntu found during install?

btw.. why two XP partitions?

---

