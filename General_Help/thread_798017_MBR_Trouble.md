---
title: "MBR Trouble"
date: 2008-05-17
forum: General Help
---

### Post by bobe13 on 2008-05-17
First post under these forums, so please disregaurd if I mess something up in this post, or posted this in the wrong place >.<

So, I installed XP, then installed Ubuntu 7.04, upgraded it to 8.04, got all the 8.04 updates, then installed BackTrack 3 Beta ([http://www.remote-exploit.org/backtrack.html](http://www.remote-exploit.org/backtrack.html)), keeping the Ubuntu MBR.  Now, whenever I load up my computer, it pops up with a listing like the one below.

Ubuntu 8.04
Ubuntu 8.04 Safe Mode
Ubuntu 8.04
Ubuntu 8.04 Safe Mode
Ubuntu 8.04
Ubuntu 8.04 Safe Mode
Ubuntu 8.04 MemTest
Other Operating Systems
Windows XP

Now, what I'm hoping to be able to do is set it up to where all I see is a list like this:

Ubuntu 8.04
Windows XP
BackTrack

Only problem is, I have no idea where to start or even what to do to help this.  I know a little about computers, but not much, so if anyone is able to help me out, please and thank you.  =P

---

### Post by TeoBigusGeekus on 2008-05-17
Please post us the content of your menu.lst file
```
gksudo gedit /boot/grub/menu.lst
```
(.LST)

---

### Post by bobe13 on 2008-05-17
Completely empty, if I did it right.

---

### Post by TeoBigusGeekus on 2008-05-17
Can't be... Are you sure you typed menu.lst(LST) and not menu.1st(1ST)?

---

### Post by bobe13 on 2008-05-17
Worked 2nd time, here it is.  Didn't type wrong, just didn't show anything >.<

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
# kopt=root=UUID=ad9db3c8-2de4-4cd5-a617-a2836277e9dd ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ad9db3c8-2de4-4cd5-a617-a2836277e9dd ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ad9db3c8-2de4-4cd5-a617-a2836277e9dd ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ad9db3c8-2de4-4cd5-a617-a2836277e9dd ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ad9db3c8-2de4-4cd5-a617-a2836277e9dd ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by TeoBigusGeekus on 2008-05-17
These lines
```
title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ad9db3c8-2de4-4cd5-a617-a2836277e9dd ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ad9db3c8-2de4-4cd5-a617-a2836277e9dd ro single
initrd		/boot/initrd.img-2.6.22-14-generic
```

comment them out

```
#title		Ubuntu 8.04, kernel 2.6.22-14-generic
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.22-14-generic #root=UUID=ad9db3c8-2de4-4cd5-a617-a2836277e9dd ro quiet splash
#initrd		/boot/initrd.img-2.6.22-14-generic
#quiet

#title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.22-14-generic #root=UUID=ad9db3c8-2de4-4cd5-a617-a2836277e9dd ro single
#initrd		/boot/initrd.img-2.6.22-14-generic
```

and save the file. You don't need an older kernel to show up in your grub menu, but keep it in the file for safety reasons.

As for backtrack, there doesn't seem to be any sign of it...

---

### Post by bobe13 on 2008-05-17
Thanks for helping me with that part =P

The BackTrack though..  I don't know how I would add that into the boot menu.  Any ideas for that?  It's under /sda/hda3/  I think, or something like that.  I know XP has a 1 on the end, Ubuntu has a 2, BackTrack has a 3, and my swap has a 4.  I'll check more in detail in a little, had to get off tri booting computer for a little, but any help on adding backtrack would be greatly appreciated =P

---

### Post by TeoBigusGeekus on 2008-05-18
Add this at the end of the menu.lst file

```
title BackTrack
root (hd0,2)
kernel /boot/vmlinuz ro root=/dev/sda3
boot
```

cross your fingers and reboot.

---

