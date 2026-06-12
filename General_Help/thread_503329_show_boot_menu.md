---
title: "show boot menu"
date: 2007-07-17
forum: General Help
---

### Post by cccc on 2007-07-17
hi

I have ubuntu 7.04 Feisty Fawn with all updates installed:```

uname -a
Linux ania 2.6.20-16-386 #2 Thu Jun 7 20:16:13 UTC 2007 i686 GNU/Linux

```

during the startup I get a black screen.
howto configure to show Boot Messages during startup ?

kind regards
cccc

---

### Post by Medieval_Creations on 2007-07-17
By Boot menu, I assume you mean GRUB.  The screen just after the BIOS where you can choose which OS to start.

All you need to do is edit the menu.lst file in /boot/grub folder.
You are going to look for a line that says hiddenmenu and comment it out with a #.

Command to edit the menu:
sudo gedit /boot/grub/menu.lst

```

# hiddenmenu

```

---

### Post by cccc on 2007-07-19
I changed, but it doesn't work.

---

### Post by reckless2k2 on 2007-07-19
verify that the file has been changed and then reboot. if you didn't sudo or save, then the file never changed and it wouldn't work.

---

### Post by cccc on 2007-07-19
I have:```

# cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=9e29b970-e8fb-4824-b6db-cea685f836e5 ro

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

title           Ubuntu, kernel 2.6.20-16-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-386 root=UUID=9e29b970-e8fb-4824-b6db-cea685f836e5 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-386
savedefault

title           Ubuntu, kernel 2.6.20-16-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-386 root=UUID=9e29b970-e8fb-4824-b6db-cea685f836e5 ro single
initrd          /boot/initrd.img-2.6.20-16-386

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```
but it doesn't work !

---

### Post by reckless2k2 on 2007-07-19
are you still getting the "esc" menu when you start to show your grub menu? do you have more than one OS on your system? are you talking about BIOS of GRUB?

kill the 2nd question since i looked at your grub and saw it's only ubuntu. hahaha./

---

### Post by cccc on 2007-07-19
sorry, I think my question wasn't clear.  
I get a boot menu for a few seconds, but I'm still missing Boot Messages on the screen.

---

### Post by Medieval_Creations on 2007-07-19
Try increasing the "timeout" time.  This is the time Grub waits and will then boot the default OS.
According to your post it's currently set to 3 seconds.
```
timeout         3
```

Change is to something like 15.
```
timeout         15
```

This shoud give you more time to look at the different options.

---

### Post by cccc on 2007-07-19
sorry for the mistake, but boot menu is not so important for me,
I'd like to have BOOT TEXT (all startup commands) on the screen during system start.

---

### Post by reckless2k2 on 2007-07-19
ok i think you are talking about the BIOS. you'll have to access the BIOS using esc or del...i'm not sure how you do it on your system. a try or google might help. anyway, once inside, you'll have to change the boot argument to show full boot sequence. the wording is different in each BIOS. again, some googling on your PC or motherboard will help on all that.

---

### Post by cccc on 2007-07-19
> **reckless2k2 said:**
> ok i think you are talking about the BIOS. you'll have to access the BIOS using esc or del...i'm not sure how you do it on your system. a try or google might help. anyway, once inside, you'll have to change the boot argument to show full boot sequence. the wording is different in each BIOS. again, some googling on your PC or motherboard will help on all that.

NOT the BIOS, I mean to get Boot Text (Boot Messages) on the screen during startup.
my screen is black during the startup.
I can see Boot Messages if I press CTRL-ALT-F1, but howto get it automatically ?

---

### Post by cccc on 2007-07-19
I solved this problem.

I changed in /boot/grub/menu.lst 

from:```


# defoptions=quiet splash

kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=9e29b970-e8fb-4824-b6db-cea685f836e5 ro quiet splash 


```
to:```

# defoptions=

kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=9e29b970-e8fb-4824-b6db-cea685f836e5 ro

```
and now it works great !

greetings
cccc

---

