---
title: "Grub Install Woes"
date: 2008-04-28
forum: General Help
---

### Post by WastingBody on 2008-04-28
After I installed Hardy I reinstalled Gutsy on another partition because of wireless issues I was having at the time. I knew I could get wireless to work in Gutsy. Well when Gutsy installed it installed it's grub. I have a separate boot partition set up, but its not being used as of now. When I try to install grub using root(hd0,0); setup (hd0,0) it goes straight to bash on boot, so I have reinstall using root(hd0,5); setup(hd0) then the Gutsy grub loads. I'm not sure how to get grub to work on the first partition. I thought someone here could help me out.

Thanks

---

### Post by TeoBigusGeekus on 2008-04-28
Post us the output of 

```
sudo fdisk -l
```


and the contents of your menu.lst

so that we can have a look.

---

### Post by WastingBody on 2008-04-28
```
Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000437be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391   83  Linux
/dev/sda2              14         163     1204875   82  Linux swap / Solaris
/dev/sda3             164        1729    12578895    5  Extended
/dev/sda5             164        1207     8385898+  83  Linux
/dev/sda6            1208        1729     4192933+  83  Linux

```

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
# kopt=root=UUID=bdf8ecfc-a80a-426e-a5fd-27cc1fd2c94d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bdf8ecfc-a80a-426e-a5fd-27cc1fd2c94d ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bdf8ecfc-a80a-426e-a5fd-27cc1fd2c94d ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/sda5)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=aa602c6f-5664-4054-8390-7824e1eca4dd ro quiet splash 
initrd		/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda5)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=aa602c6f-5664-4054-8390-7824e1eca4dd ro single 
initrd		/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04, memtest86+ (on /dev/sda5)
root		(hd0,0)
kernel		/memtest86+.bin  
savedefault
boot

```

The other menu.lst is the exact same just without the Gutsy entries.

---

### Post by TeoBigusGeekus on 2008-04-28
Can you boot into both Hardy and Gutsy?

---

### Post by WastingBody on 2008-04-28
Yes, Grub works fine and I can boot into Gutsy and Hardy.

---

### Post by WastingBody on 2008-05-01
I got it working the way I wanted it to via the Super Grub Disk. It made the install very easy. :P

---

