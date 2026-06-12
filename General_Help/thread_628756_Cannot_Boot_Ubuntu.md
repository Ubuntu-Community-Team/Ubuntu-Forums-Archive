---
title: "Cannot Boot Ubuntu"
date: 2007-12-01
forum: General Help
---

### Post by ExBuM on 2007-12-01
Hi, I was messing around with the boot screen last night and I think I messed something up because now when I try to boot ubuntu I get this:

[    12.728377] Kernel panic - not syncing:
VFS: Unable to mount root fs on unknown - block (0,0)

Does anyone know how to fix this?

Here's my boot/grub/menu.lst :/ 
I think the problem might be there. >.>

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
# kopt=root=UUID=fea415c3-c430-46ab-9230-abef369805b3 ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fea415c3-c430-46ab-9230-abef369805b3 ro splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fea415c3-c430-46ab-9230-abef369805b3 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by ijason on 2007-12-01
the problem looks like it's down near the bottom, where it says : 

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

try changing it to "root   (hd0,1)" 

usually, the #,# equates to IDE channels, and then partition numbers. so 0,1 would equate to the device on ide channel 0 - the first channel - and partition number 1. i think it may be hiccuping because it's looking for a zero partition number, which is the (i believe) entire physical drive address, and doesn't have a boot record because it's not a partition.

---

### Post by ijason on 2007-12-01
you can probably find good advice - if more doesn't show up here - by searching for loader.lst, and dual booting threads. :)

---

### Post by ExBuM on 2007-12-01
Isn't that part for my windows partition?

---

### Post by Craigus on 2007-12-01
> i think it may be hiccuping because it's looking for a zero partition number, which is the (i believe) entire physical drive address, and doesn't have a boot record because it's not a partition.

In grub, the first partition is 0 (not 1), so hd0,0 is the first partition on the first drive.

What did you change in menu.lst, and what is actually on your second partition (ie hd0,1) ?

---

### Post by solarwind on 2007-12-01
Well, I think you should be able to boot into the live cd and regenerate the grub list. That's what I did when I had a similar problem and it worked.

---

### Post by ExBuM on 2007-12-01
I remember changing 
```
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fea415c3-c430-46ab-9230-abef369805b3 ro splash
``` 
by getting rid of "quiet" and maybe something else.
I also replaced the original boot screen with something else.

I think my second partition is probably just music or something.

> **solarwind said:**
> Well, I think you should be able to boot into the live cd and regenerate the grub list. That's what I did when I had a similar problem and it worked.

How do you do that? :O

---

### Post by Craigus on 2007-12-01
Here's some discussion:

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by ExBuM on 2007-12-01
Ok thanks I'll be trying that.

---

### Post by teryowen on 2007-12-01
boot off a live CD, in terminal do the following:

grub
root (hd0,2)
setup (hd0)
quit

reboot without cd should work

---

### Post by ExBuM on 2007-12-01
> **teryowen said:**
> boot off a live CD, in terminal do the following:

grub
root (hd0,2)
setup (hd0)
quit

reboot without cd should work
I just followed the other guide and did that. Unfortunately it wasn't fixed so I still can't boot. I saw your post and thought I'd try it again and now I'm getting "Error 21: Selected disk does not exist" at the root (hd0,2) part.

Edit: Nevermind, if I type in sudo grub at the beginning then it's okay. But it still doesn't fix the "kernel panic"

---

### Post by teryowen on 2007-12-01
post output of:

sudo fdisk -l

( -l is a lowercase L)

---

### Post by ExBuM on 2007-12-01
```
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06d306d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       13662    58540860    f  W95 Ext'd (LBA)
/dev/sda3           13663       19452    46508175   83  Linux
/dev/sda5            6375       13409    56508606    7  HPFS/NTFS
/dev/sda6           13410       13662     2032191   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x58da5ad8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       19452   156240157+   f  W95 Ext'd (LBA)
/dev/sdb5               2        6503    52227283+   7  HPFS/NTFS
/dev/sdb6            6504       13005    52227283+   7  HPFS/NTFS
/dev/sdb7           13006       19452    51785496    7  HPFS/NTFS

```

---

### Post by teryowen on 2007-12-01
hmm, everything seems alrite, you remember how you said you changed a line in your menu.lst file, perhaps you should add the "quite" part to the end of the kernel line, mine looks like this,

kernel                /boot/vmlinuz-2.6.22-14-generic root=UUID=b6b601cc-c069-40e6-b448-c96100eba669 ro quiet splash 

so just add back that quiet part not sure if it will fix anything

---

### Post by ExBuM on 2007-12-01
Adding quiet eliminated a lot of random errors but the kernel panic thing is still there xD

Could if have something to do with the boot screen or something? How do you restore the default boot screen with a live CD?

---

### Post by teryowen on 2007-12-01
Sorry wish i could help, but i dont how. post another thread about kernel panic

---

### Post by ExBuM on 2007-12-01
Alright it's fine. Thanks a lot for your help though ^^

---

### Post by jken146 on 2007-12-01
[http://ubuntuforums.org/showthread.php?t=622002](http://ubuntuforums.org/showthread.php?t=622002) is my story with a similar problem.  That thread contains links to a couple of other threads that may be useful.

---

### Post by ExBuM on 2007-12-01
> **jken146 said:**
> [http://ubuntuforums.org/showthread.php?t=622002](http://ubuntuforums.org/showthread.php?t=622002) is my story with a similar problem.  That thread contains links to a couple of other threads that may be useful.

I actually saw that thread before I posted this one. I'm not really sure what to do because I don't have a vga-792 in that line. Also I don't know if some of those commands are for your computer or if they work on everyone's :/ (I'm a linux noob :confused:)

I started getting this error message after trying to install :[http://gnome-look.org/content/show.php?content=61617&forumpage=0](http://gnome-look.org/content/show.php?content=61617&forumpage=0)
(Actually I'm not sure if it was caused by my attempt at installing that but I think most likely that is the reason)

---

### Post by teryowen on 2007-12-01
maybe this will help:

boot of the live CD, and copy the original image files into the boot directory like:
vmlinuz-2.6.22-14-generic
initrd.img-2.6.22-14-generic

and all the other files, just dont touch the GRUB folder.

EDIT: replace the ones that are on there with the fresh ones of your live CD, be careful with this im not to certain but i remember reading about the same problem and it fixed it like this. make a back up of the stuff ur replacing

---

### Post by ExBuM on 2007-12-01
Ah it still didn't fix it. I wish I remembered what I did to cause this... -_-
Is there a way to reinstall ubuntu without losing already installed applications and stuff?

---

