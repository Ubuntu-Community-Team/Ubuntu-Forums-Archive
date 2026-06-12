---
title: "Working with GRUB"
date: 2008-03-19
forum: General Help
---

### Post by bobabot1 on 2008-03-19
Hi all!

I've been searching these forums and unfortunately, either my situation is unique to the point where I'm having trouble finding a solution to bend to my will, I am not correctly using said solutions, or I really need to work on my search-fu.

In any case, here is my problem:

I have just reinstalled winxp because I need it for my band. It booted fine and I was able to restore GRUB and boot into my beloved ubuntu partition. Unfortunately, I am having trouble making an entry for my windows option; the one I tried did not work.

Here are my specs.
```

/dev/sda1 <-- Ubuntu partition
/dev/sda2 <-- Winxp partition 1
```

Here is my menu.lst in which everything works but the last entry, the winxp entry:

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=c8e4abc8-6cfc-4d62-9300-759900240c4a ro

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

title		Ubuntu, kernel 2.6.20-16-realtime
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-realtime root=UUID=c8e4abc8-6cfc-4d62-9300-759900240c4a ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-realtime
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-realtime (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-realtime root=UUID=c8e4abc8-6cfc-4d62-9300-759900240c4a ro single
initrd		/boot/initrd.img-2.6.20-16-realtime

title		Ubuntu, kernel 2.6.20-16-lowlatency
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-lowlatency root=UUID=c8e4abc8-6cfc-4d62-9300-759900240c4a ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-lowlatency
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-lowlatency (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-lowlatency root=UUID=c8e4abc8-6cfc-4d62-9300-759900240c4a ro single
initrd		/boot/initrd.img-2.6.20-16-lowlatency

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=c8e4abc8-6cfc-4d62-9300-759900240c4a ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=c8e4abc8-6cfc-4d62-9300-759900240c4a ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=c8e4abc8-6cfc-4d62-9300-759900240c4a ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=c8e4abc8-6cfc-4d62-9300-759900240c4a ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title 		Windows XP
root 		(hd0,1)
makeactivechainloader +1 


### END DEBIAN AUTOMAGIC KERNELS LIST
```

What's really getting me is the whole root (hdx,x) crap.

Any help would be much appreciated.

Thank you!

---

### Post by Shazaam on 2008-03-19
Change this......
```
makeactivechainloader +1 
```
to this.....
```
makeactive
chainloader +1
```
Post back with your results.

---

### Post by bobabot1 on 2008-03-19
Okey doke. Will try.

---

### Post by bobabot1 on 2008-03-19
Alright. That worked... sort of.

It booted windows, ut with all the settings and files that were on my /dev/sda4 partition.

Do you have any idea why it would do such a thing?

---

