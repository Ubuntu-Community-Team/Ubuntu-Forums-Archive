---
title: "argh 2 big problems"
date: 2007-08-25
forum: General Help
---

### Post by tommyboi199uk on 2007-08-25
first my major problem is i can not dual boot into windows it just restarts the computer! and i crnt open a dvd game it says wrong mount volume or summit :confused: helpme or im gonna have to re boot the comp back on windows! plz help me!!1

---

### Post by expatCM on 2007-08-25
What "just restarts the computer", what do you see happen?

Do you see the Grub menu when you start up the system?

---

### Post by tommyboi199uk on 2007-08-25
the grub selection thingy comes up i select winxp and it shows the start up page for a scond but then goes back into the bios then to the grub selection and i only can go on one of the four ubuntu options

---

### Post by apetresc on 2007-08-25
> **tommyboi199uk said:**
> the grub selection thingy comes up i select winxp and it shows the start up page for a scond but then goes back into the bios then to the grub selection and i only can go on one of the four ubuntu options

Okay, this is most likely a fixable problem. Could you describe your hard drive layout to us (basically, how it's partitioned, and which partition Windows is installed on), and also paste the contents of your /boot/grub/menu.lst file?

---

### Post by tommyboi199uk on 2007-08-25
> **AdrianP said:**
> Okay, this is most likely a fixable problem. Could you describe your hard drive layout to us (basically, how it's partitioned, and which partition Windows is installed on), and also paste the contents of your /boot/menu/grub.lst file?

do you mean boot/grub/menu.lst because thats closest i can find

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
# kopt=root=UUID=e7e8fae8-beae-45c0-9e39-ce035de04259 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e7e8fae8-beae-45c0-9e39-ce035de04259 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e7e8fae8-beae-45c0-9e39-ce035de04259 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e7e8fae8-beae-45c0-9e39-ce035de04259 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e7e8fae8-beae-45c0-9e39-ce035de04259 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


there it is anyways

---

### Post by apetresc on 2007-08-25
> **tommyboi199uk said:**
> do you mean boot/grub/menu.lst because thats closest i can find Oops, silly typo :) Yes, that is what I meant.

Your GRUB loader is looking for windows on the first partition of the first hard drive. To see if this is correct, give us the output of: ```
sudo fdisk -l /dev/hda
```

---

### Post by tommyboi199uk on 2007-08-25
> **AdrianP said:**
> Oops, silly typo :) Yes, that is what I meant.

Your GRUB loader is looking for windows on the first partition of the first hard drive. To see if this is correct, give us the output of: ```
sudo fdisk -l /dev/hda
```

Cannot open /dev/hda: No application is known for this kind of file

:mad:

---

### Post by apetresc on 2007-08-25
> **tommyboi199uk said:**
> Cannot open /dev/hda: No application is known for this kind of file

:mad:
Okay then, try ```
sudo fdisk -l /dev/sda
```

---

### Post by tommyboi199uk on 2007-08-25
> **AdrianP said:**
> Okay then, try ```
sudo fdisk -l /dev/sda
```

sorry bout the delay 

it comes up in text editor some reason and on it is just a blank screen which application should i use to open it with

---

### Post by aysiu on 2007-08-25
Closed at [the request of the OP](http://ubuntuforums.org/showthread.php?t=534567)

---

