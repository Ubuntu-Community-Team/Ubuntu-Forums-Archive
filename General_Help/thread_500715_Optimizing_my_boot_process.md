---
title: "Optimizing my boot process"
date: 2007-07-14
forum: General Help
---

### Post by hackle577 on 2007-07-14
Lately I've been obsessed with doing whatever it take to optimize my bootup time, which is relatively slow. But it seems that whatever I do, my laptop still takes longer than it should to start. Here's my info:

Dell Inspiron 4150
Ubuntu 7.04
1.7 GHz Pentium 4 processor
640 MB RAM

My boot time is 1:22 to get to the desktop, and about 1:35 before the desktop become usable.

fdisk -l
```
Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         912     7325608+  83  Linux
/dev/sda2             913        3526    20996955   83  Linux
/dev/sda3            3527        3648      979965   82  Linux swap / Solaris
```

/boot/grub/menu.lst
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
# kopt=root=UUID=abcf0336-0006-425e-9f3f-f122c86d83bf ro

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
# defoptions=quiet splash rootflags=data=writeback

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
# altoptions=(recovery mode) single rootflags=data=writeback

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=abcf0336-0006-425e-9f3f-f122c86d83bf ro rootflags=data=writeback
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=abcf0336-0006-425e-9f3f-f122c86d83bf ro single rootflags=data=writeback
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=abcf0336-0006-425e-9f3f-f122c86d83bf ro quiet splash rootflags=data=writeback
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=abcf0336-0006-425e-9f3f-f122c86d83bf ro single rootflags=data=writeback
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Also, I've attached a bootchart log of my boot process. Oddly, the single part of booting that I think takes longer than it should is GNOME. Once I login, it seems to hang for a bit before the desktop starts loading. Is there anything I can do about this? I've gone through most of the guides, tweaks, etc. but sometimes I don't really notice any difference.

Thanks!

---

### Post by dreadlord_chris on 2007-07-14
According to that chart your boot process took 38 seconds - that's pretty typical. Note, though, bootchart only monitors up to the start of your desktop manager (GDM/KDM/etc)

Sounds to me like you're more interested in speeding up the loading of your Desktop
.wysiwyg { background-attachment: scroll; background-repeat: repeat; background-position: 0% 0%; background-color: #ffffff; background-image: none; color: #666666; font-family: "Arial [monotype]", "Arial [monotype]", "Helvetica [Adobe]", "Arial [monotype]"; font-style: normal; font-variant: normal; font-weight: 400; font-size: 10pt; line-height: normal } p { margin: 0px; }

---

### Post by hackle577 on 2007-07-14
Does GNOME usually take that long to load? Maybe I just haven't noticed it before...

---

### Post by dreadlord_chris on 2007-07-14
so, Gnome takes about a minute to load your desktop *after* you get to the log in screen?

 Doesn't really seem all that long to me....
 .wysiwyg { background-attachment: scroll; background-repeat: repeat; background-position: 0% 0%; background-color: #ffffff; background-image: none; color: #666666; font-family: "Arial [monotype]", "Arial [monotype]", "Helvetica [Adobe]", "Arial [monotype]"; font-style: normal; font-variant: normal; font-weight: 400; font-size: 10pt; line-height: normal } p { margin: 0px; }

---

### Post by hackle577 on 2007-07-14
No, it takes me about 1:20 to get to the login, and about 20 more seconds to get to a usable desktop.

I don't think the bootchart time of 38 seconds is accurate because I timed it myself 3 times.

---

### Post by dreadlord_chris on 2007-07-15
> **hackle577 said:**
> No, it takes me about 1:20 to get to the login, and about 20 more seconds to get to a usable desktop.

I don't think the bootchart time of 38 seconds is accurate because I timed it myself 3 times.

huh.... bootchart works perfectly fine for me. I don't know what to tell you then....

---

