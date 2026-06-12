---
title: "Error 17 when booting?"
date: 2007-11-03
forum: General Help
---

### Post by schnauzer93 on 2007-11-03
When I try to boot wubi (7.04) I get an error 17 while loading "Kernel 2.6.20-16-generic". I've defragmented my hard drive and am still unable to boot. However, when it gives me a list of options, I am able to boot "Ubuntu (Original Kernel)". Is there any file I can edit to either resolve the error 17 or set Original Kernel as default?

---

### Post by geforce123 on 2007-11-03
yes,

Can you post the output of /boot/grub/menu.lst ?

btw, error 17 means:

# 17 : "Invalid device requested"

This error is returned if a device string is recognizable but does not fall under the other device errors.

---

### Post by ago on 2007-11-03
Try wubi 7.10

---

### Post by schnauzer93 on 2007-11-04
This is my Menu.lst file. 

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
# is the entry saved with the command 'boot'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		1

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
# kopt=root=/media/host/wubi/disks/system.virtual.disk ro
# kopt_2_6=root=/dev/hda1 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
		(hd0,0)
kernel		/vmlinuz-2.6.20-16-generic root=/dev/hda1 ro quiet splash
initrd		/initrd.img-2.6.20-16-generic
boot

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
		(hd0,0)
kernel		/vmlinuz-2.6.20-16-generic root=/dev/hda1 ro single
initrd		/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
		(hd0,0)
kernel		/vmlinuz-2.6.20-15-generic root=/dev/hda1 ro quiet splash
initrd		/initrd.img-2.6.20-15-generic
boot

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
		(hd0,0)
kernel		/vmlinuz-2.6.20-15-generic root=/dev/hda1 ro single
initrd		/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
		(hd0,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title Ubuntu (Original Kernel)
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux setup_iso=ubuntu-7.04-alternate-i386.iso quiet splash ro acpi=off
initrd /wubi/boot/initrd
boot

```

By the way, I'm a little nervous about installing alpha software on my computer, so I'd kind of like to stick to 7.04 for a while.

EDIT: I've installed 7.10, but it says I have to run chkdsk /r. I've done that, and it still says I have to run chkdsk.

EDIT 2: This is what my disk fragmentation looks like with wubi:

[IMG]http://i150.photobucket.com/albums/s96/licktheboard/withwubi.gif[/IMG]

And without wubi:

[IMG]http://i150.photobucket.com/albums/s96/licktheboard/withoutwubi.gif[/IMG]

---

### Post by ago on 2007-11-05
Uninstall any previous version of wubi. Run chkdsk /r then reboot into windows. Run chkdsk in r/o mode to see that everything is ok. Then reinstall 7.10.

---

