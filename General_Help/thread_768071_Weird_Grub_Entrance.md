---
title: "Weird Grub Entrance"
date: 2008-04-26
forum: General Help
---

### Post by lrich28 on 2008-04-26
For some reason I have a listing that is Hardy Heron 386.  The one I use is below it called Hardy Heron generic.  How to I get rid of the first listing?

---

### Post by tamoneya on 2008-04-26
look at the bottom of your /boot/grub/menu.lst file and delete (I recommend commenting out) the necessary lines.  If it isnt self explainatory just post /boot/grub/menu.lst here and we will help you out.

---

### Post by IndyGunFreak on 2008-04-26
> **tamoneya said:**
> look at the bottom of your /boot/grub/menu.lst file and delete (I recommend commenting out) the necessary lines.  If it isnt self explainatory just post /boot/grub/menu.lst here and we will help you out.

Agree, always comment out, don't delete.

---

### Post by lrich28 on 2008-04-26
For some reason when I enter that in a terminal all I get is Permission Denied.  Sudo doesn't help, it just says command not found.  Help?

---

### Post by phillip_style on 2008-04-26
Sorry to hijack this thread but I have a very similar problem. I have vista on a 200gb drive and ubuntu 8.04 on an 80gb driver. I used to have 7.10 on this 80gb drive and had too many issues so I started with a fresh install of 7.10 I told the install to use the entire disk (thinking that it would clean off the old install and install the new one fresh). After I install 7.10 again it asked me to upgrade to 8.04 so I did. No problems and 8.04 is working a charm.
However my grub has three entries 2 ubuntu and 1 windows vista.
The top most on the list is 8.04 which is all good however the second one was my old install which has had its day and has booting issues and last but not least vista.

Please see the code below from my menu.lst:
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
# kopt=root=UUID=fa82f6a1-1a3c-4cfb-ab75-16be41126c0e ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fa82f6a1-1a3c-4cfb-ab75-16be41126c0e ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fa82f6a1-1a3c-4cfb-ab75-16be41126c0e ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fa82f6a1-1a3c-4cfb-ab75-16be41126c0e ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fa82f6a1-1a3c-4cfb-ab75-16be41126c0e ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Am I right in say I just need to change the following:

```
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fa82f6a1-1a3c-4cfb-ab75-16be41126c0e ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fa82f6a1-1a3c-4cfb-ab75-16be41126c0e ro single
initrd		/boot/initrd.img-2.6.24-16-generic

#title		Ubuntu 8.04, kernel 2.6.22-14-generic
#root		(hd2,0)
#kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fa82f6a1-1a3c-4cfb-ab75-16be41126c0e ro quiet splash
#initrd		/boot/initrd.img-2.6.22-14-generic
#quiet

#title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
#root		(hd2,0)
#kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fa82f6a1-1a3c-4cfb-ab75-16be41126c0e ro single
#initrd		/boot/initrd.img-2.6.22-14-generic

#title		Ubuntu 8.04, memtest86+
#root		(hd2,0)
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

Thanks,
Phil

---

### Post by phillip_style on 2008-04-27
Anyone?

---

### Post by IndyGunFreak on 2008-05-03
> **phillip_style said:**
> Anyone?

Yes..

I would just double check by booting, that that entry is the one that works to boot 8.04.  Its likely only 1 of them works, and the others don't.  So if you're using the "First" Hardy option in your Grub menu, then you should be fine w/ what you're doing below.

---

