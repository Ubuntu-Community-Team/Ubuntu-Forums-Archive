---
title: "Grub  error 11 when trying to boot Ubuntu"
date: 2007-12-04
forum: General Help
---

### Post by Kaze3 on 2007-12-04
Hi,

I am currently dual booting XP and Ubuntu. I just tried to boot into Ubuntu after using Windows exclusively for a week or so. I now get error 11  if i try to select Ubuntu in grub. I'm not completely new to Linux but this is well beyond me. 

I asked a friend to see if he could figure out what is going on. He says that i'm missing some files from the /dev/ folder, namely some called hda or sda? I originally thought it was my menu.lst file since i've edited it recently to comment out some of the entries but everything seems fine. 

Has anyone got any other suggestions as to what to do?

Thanks,

Matt

---

### Post by logos34 on 2007-12-04
Boot from the ubuntu live cd and post your menu.lst. And the output of 

sudo fdisk -l

---

### Post by Kaze3 on 2007-12-04
here's the menu.lst

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
# kopt=root=UUID=635b1074-038b-4040-a50a-cf2a53432391 ro

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

title		Ubuntu 7.10 Gutsy Gibbon
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

#title		Ubuntu 7.10, kernel 2.6.22-14-generic
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=635b1074-038b-4040-a50a-cf2a53432391 ro quiet splash
#initrd		/boot/initrd.img-2.6.22-14-generic
#quiet

#title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=635b1074-038b-4040-a50a-cf2a53432391 ro single
#initrd		/boot/initrd.img-2.6.22-14-generic

#title		Ubuntu 7.10, kernel 2.6.22-13-generic
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.22-13-generic root=UUID=635b1074-038b-4040-a50a-cf2a53432391 ro quiet splash
#initrd		/boot/initrd.img-2.6.22-13-generic
#quiet

#title		Ubuntu 7.10, kernel 2.6.22-13-generic (recovery mode)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.22-13-generic root=UUID=635b1074-038b-4040-a50a-cf2a53432391 ro single
#initrd		/boot/initrd.img-2.6.22-13-generic

#title		Ubuntu 7.10, kernel 2.6.22-12-generic
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=635b1074-038b-4040-a50a-cf2a53432391 ro quiet splash
#initrd		/boot/initrd.img-2.6.22-12-generic
#quiet

#title		Ubuntu 7.10, kernel 2.6.22-12-generic (recovery mode)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=635b1074-038b-4040-a50a-cf2a53432391 ro single
#initrd		/boot/initrd.img-2.6.22-12-generic

#title		Ubuntu 7.10, memtest86+
#root		(hd0,1)
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windoze XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

and the output from sudo fdisk -l

```
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeef0eef0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3586    28804513+   7  HPFS/NTFS
/dev/sda2            3587        4757     9406057+  83  Linux
/dev/sda3            4758        4864      859477+   5  Extended
/dev/sda5            4758        4864      859446   82  Linux swap / Solaris
```

---

### Post by Kaze3 on 2007-12-04
I've just had a thought.

I have recently resized the partitions with a gparted live disc to give XP more space. I can't remember if i've tried to boot Ubuntu since i did that so i'm not sure if its relevant.

---

### Post by logos34 on 2007-12-04
I notice that it's the only one using the 'dev' format instead of UUID...Replace 'root=/dev/sda2' on the kernel line with 'UUID=###", same as others.  Normally only windows refuses to boot after being resized (until you run chkdsk that is)...linux doesn't seem to finicky in that respect, but you could try running sudo fsck /dev/sda2.

---

### Post by SuperAndy on 2007-12-04
```
# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
root
```

Got root? :P

either comment out or delete that extra root, and you should be set.

---

### Post by Kaze3 on 2007-12-04
The uncommented root was the problem. Cheers guys

---

