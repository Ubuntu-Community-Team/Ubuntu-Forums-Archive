---
title: "EASY Grub Menu Question!!!"
date: 2007-11-08
forum: General Help
---

### Post by kshane on 2007-11-08
I made some changes to my Grub menu (menu.lst) and am happy with the outcome, but I have two questions about it.

First, I would like to have the boot process stop there at the menu without the timer.  So that if you don't choose an OS it just stays there and waits.  If I set the timer to "0", it just boots to the first option.  I don't want a timer going on it at all.

Second, I enabled the colors and the only option that is visible is the first, unless you arrow down.  As you arrow down the other options become visible as you arrow to/past them.  Is there a way to have the entire menu visible initially?

Thanks!

Kevin

---

### Post by bodhi.zazen on 2007-11-08
for the first I *think* that you just comment out the timeout line (add a # at the front)

for the second, disable, ie comment out, hidden menu

---

### Post by kshane on 2007-11-08
> **bodhi.zazen said:**
> for the first I *think* that you just comment out the timeout line (add a # at the front)

for the second, disable, ie comment out, hidden menu

Yes, you are correct on the timer.  Thanks!!!

I think the modifications I made to the menu are what's making the remaining lines invisible until they highlighted by arrowing down.  I changed it back to the default (b/w) and it still does it.  Any ideas there?  Here's a copy of my menu.lst to peruse...  I will be off line for an hour or so after this...

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
#timeout		100

## hiddenmenu
## Hides the menu by default (press ESC to see the menu)
##hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=c1dd7906-ecf3-403c-8348-9701b828e691 ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c1dd7906-ecf3-403c-8348-9701b828e691 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		 
root

title Elive Gem  
# kernel path-to-kernel root=rootdevice kernelarguments
root (hd0,4)
kernel /boot/vmlinuz-2.6.18-elive root=/dev/hda5 vga=791 splash=silent
initrd /boot/initrd.img-2.6.18-elive

#title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c1dd7906-ecf3-403c-8348-9701b828e691 ro single
#initrd		/boot/initrd.img-2.6.22-14-generic

#title		Ubuntu 7.10, memtest86+
#root		(hd0,1)
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.


title		 
root


title		Other operating systems:
root

title		 
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windblows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

Thanks a whole lot!  

Kevin

---

