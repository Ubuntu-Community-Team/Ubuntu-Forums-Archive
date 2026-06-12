---
title: "[SOLVED] Lock-up after power loss."
date: 2007-11-15
forum: General Help
---

### Post by RAMDrive on 2007-11-15
I'm running 7.10 on a dell GX260, I wasn't having problems until a powerless yesterday.  Now ubuntu starts loading then goes to a black screen and locks up.  I am able to choose the recovery mode from GRUB, but I don't know where to go from there.

Is there a way to figure out what is keeping ubuntu to loading, or any other suggestions? I would prefer not to reinstall as this is the second time this has happened.   I have learned that if we can get this fixed I'm making a back-up.

thanks for any help.

---

### Post by PmDematagoda on 2007-11-15
It could be that your X-server is malfunctioning, try this in a terminal:-

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and see if that will solve your problem.

---

### Post by RAMDrive on 2007-11-15
> **PmDematagoda said:**
> It could be that your X-server is malfunctioning, try this in a terminal:-

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and see if that will solve your problem.

did that and selected two resolutions I new my system could run, hit enter then received this "xserver-xorg postinst warning: overwriting possibly-costomised configuration file; backup in /etc/X11/xorg.conf.20071115095826"

---

### Post by PmDematagoda on 2007-11-15
That message is normal, did you check if the Ubuntu 7.10 GUI was fixed?

---

### Post by RAMDrive on 2007-11-15
Nope, that didn't work either.

 I then ran sudo dpkg-reconfigure xserver-xorg and went through the steps without luck.  However I noticed that I'm not getting the ubuntu splash screen after grub.

---

### Post by PmDematagoda on 2007-11-15
Ok, then the issue may be with the Ubuntu splash, do:-
```

gedit /boot/grub/menu.lst

```
in Recovery Mode and post the file.

---

### Post by RAMDrive on 2007-11-15
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
# kopt=root=UUID=89798548-2ceb-4e7c-92bf-6b9504e5b50b ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=89798548-2ceb-4e7c-92bf-6b9504e5b50b ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=89798548-2ceb-4e7c-92bf-6b9504e5b50b ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by PmDematagoda on 2007-11-15
Ok, in this entry:-

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=89798548-2ceb-4e7c-92bf-6b9504e5b50b ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

Delete the words "quiet" and "splash" on this particular line:-

kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=89798548-2ceb-4e7c-92bf-6b9504e5b50b ro quiet splash

Then reboot and see if that solves your problem.

---

### Post by RAMDrive on 2007-11-15
Thanks, I'll give that a try when I'm back in the office in the morning.

---

### Post by RAMDrive on 2007-11-16
*It's Alive ... It's Alive!*




starting back-up of system...

---

### Post by PmDematagoda on 2007-11-16
Glad to hear that you got it to work:).

Edit:- Oh yes one more thing, could you mark this thread "Solved" so that it could benefit others with similar problems?

---

