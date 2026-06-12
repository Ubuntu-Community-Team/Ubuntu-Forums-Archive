---
title: "GRUB Error 21"
date: 2008-01-31
forum: General Help
---

### Post by Aloshi on 2008-01-31
Hello, I recently bought an external USB Hard Drive for Ubuntu 7.10 as I can't partition my main hard drive (long story...). Windows XP is currently installed on my only internal hard drive.  So I installed Ubuntu to it, booted into it fine with GRUB which was automatically installed.  However, while I was using Ubuntu, it froze completely and I was forced to do a hard reboot.  I started up my computer, and it tried to automatically use GRUB.  I was rewarded with GRUB failed to load, error 21.  I can't boot into windows OR Ubuntu because the GRUB menu won't even load.  I've booted into Ubuntu 7.10 via livecd (it's how I'm typing this message) and have access to my external hard drive (The external HDD is completely new, so I can reformat it, etc. if needed) and can modify my menu.lst in boot/grub if needed.

What my Menu.lst says:

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=4603b688-234d-41a8-b34d-2583596b8b6c ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4603b688-234d-41a8-b34d-2583596b8b6c ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4603b688-234d-41a8-b34d-2583596b8b6c ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


Any way to get GRUB working again so I can at least boot into Ubuntu or Windows XP?

---

### Post by Aloshi on 2008-01-31
Upon further inspection, it seems my computer is not detecting my USB hard drive for some reason.  Could I perhaps install GRUB to my Windows drive and have it run from there?

---

### Post by Aloshi on 2008-01-31
Well, I repaired the MBR using a Windows XP CD's recovery console.  Is there any way I can get it to run Ubuntu from my external Hard Drive?

EDIT: Interesting, I ran fdisk -l and it seems that my Hard Drive which contains XP isn't listed.
EDIT2: I tried running sudo grub-install /dev/sdb2 (Linux partition of USB Drive), and got can not find /boot: not found or not a block device.

---

### Post by imtheguru on 2008-01-31
Error 21 means "Can not find disk".

grub-install cannot be used on target devices which are NOT in block mode. One solution is to mount the device with the correct filesystem on a rw mount point, then chroot to this new mount point.

You will now be functioning off the hard disk. Then try grub-install again.

If this information is alien to you, try grub super disk.

---

