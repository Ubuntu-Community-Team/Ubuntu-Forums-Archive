---
title: "Dual Boot XP won't boot."
date: 2008-06-29
forum: General Help
---

### Post by edwford on 2008-06-29
I have Ubuntu (studio) dual booted with Windows XP. I was always fine with Ubuntu with the GUI installer but then had to use a text based one for studio, and I'm a little less confident about that. Basically I was having some problems with loading the Windows Drive in Ubuntu (I am using 2 drives, not 2 partititons) and I managed to fix that and can access all my data from the Windows XP drive, however it won't boot. I am assuming it is a result of my /boot/grub/menu.lst file being incorrectly set up. 

Here is what /boot/grub/menu.lst looks like ```
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
# kopt=root=UUID=3cdfc306-892e-45e9-81aa-372cbf337e2c ro

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

title		Ubuntu 8.04, kernel 2.6.24-19-rt
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=3cdfc306-892e-45e9-81aa-372cbf337e2c ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-rt
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-rt (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=3cdfc306-892e-45e9-81aa-372cbf337e2c ro single
initrd		/boot/initrd.img-2.6.24-19-rt

title		Ubuntu 8.04, kernel 2.6.24-16-rt
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-rt root=UUID=3cdfc306-892e-45e9-81aa-372cbf337e2c ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-rt
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-rt (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-rt root=UUID=3cdfc306-892e-45e9-81aa-372cbf337e2c ro single
initrd		/boot/initrd.img-2.6.24-16-rt

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

title		Windows XP
root		(hd0,0)
savedefault
makeactive
map		(hd1) (hd0)
map		(hd0) (hd1)
chainloader	+1


### END DEBIAN AUTOMAGIC KERNELS LIST
```

and this is the results of ```
sudo fdisk -l
```
```
Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa407bf84

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9964    80035798+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6e44e602

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4660    37431418+  83  Linux
/dev/sdb2            4661        4865     1646662+   5  Extended
/dev/sdb5            4661        4865     1646631   82  Linux swap / Solaris

``` incase that is of any help at all?

Much Appreciated.

---

### Post by VMC on 2008-06-29
> **edwford said:**
> 
...
title		Windows XP
[COLOR="Red"]root		(hd0,0)[/COLOR]
savedefault
makeactive
[COLOR="Red"]map		(hd1) (hd0)
map		(hd0) (hd1)[/COLOR]
chainloader	+1
...

   Device Boot      Start         End      Blocks   Id  System
[COLOR="Red"]/dev/sda1 [/COLOR]  *           1        9964    80035798+   7  HPFS/NTFS



I don't have Windows loaded on this machine, but it appears that you don't have to "map" your Windows partition, since its already on the first hard drive and partition.

---

