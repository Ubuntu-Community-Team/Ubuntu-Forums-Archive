---
title: "Problem starting ubuntu 6.10"
date: 2007-02-04
forum: General Help
---

### Post by Graham1 on 2007-02-04
Hi

I've got a slight problem in that I can't start Ubuntu :( (from Grub). The same happened in openSUSE so I guess it's a general problem with my laptop. However, openSUSE was on a timer so it would eventually load (after 10 seconds). Could the same be setup for Ubuntu? At the moment, I'm using an external USB keyboard to press <enter>.

:)

---

### Post by riven0 on 2007-02-04
What error does it give? And, yes, there is an automatic timer.

---

### Post by Graham1 on 2007-02-04
It doesn't give any error. The laptop keyboard just doesn't work as if it's not recognized :(. I had the same problem with openSUSE.

:)

---

### Post by Graham1 on 2007-02-05
> **riven0 said:**
> What error does it give? And, yes, there is an automatic timer.

Would you mind showing me how to set this automatic timer? 

:)

---

### Post by Graham1 on 2007-02-06
Bump ;). Can anyone help?

:)

---

### Post by entangled on 2007-02-06
Just in case no-one else replies I'll try to help.

Have a look at the file menu.list (or is it .lst) in
/boot/grub
You should be able to edit (using e.g. sudo vi) the default timeout.

I suppose your USB keyboard does work with Ubuntu as well as Suse?
Perhaps you have an unsupported keyboard on that laptop? Or does it work once you have logged in?

---

### Post by Rich78 on 2007-02-06
USB keyboards don't work in GRUB.

Try using your actual laptop keyboard and you'll probably find it'll work.

---

### Post by Graham1 on 2007-02-06
> **entangled said:**
> Have a look at the file menu.list (or is it .lst) in
/boot/grub
You should be able to edit (using e.g. sudo vi) the default timeout.

The odd thing is, it is already set to 10 but nothing happens.

> I suppose your USB keyboard does work with Ubuntu as well as Suse?
Perhaps you have an unsupported keyboard on that laptop? Or does it work once you have logged in?

The external USB keyboard works in both Ubuntu and openSUSE. The laptop keyboard works fine afterwards (i.e at logon).

:)

---

### Post by Graham1 on 2007-02-06
> **Rich78 said:**
> USB keyboards don't work in GRUB.

Try using your actual laptop keyboard and you'll probably find it'll work.

I would have thought so too but it's the other way around :confused:.

:)

---

### Post by Graham1 on 2007-02-09
Anyone got any ideas otherwise I will have to go back to openSUSE. Here is the output of my menu.lst if that helps :).

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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
# kopt=root=UUID=c1965eaa-968d-4f51-a400-cbad4308645d ro
# kopt_2_6=root=/dev/hda2 ro

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

title		Ubuntu 6.10
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu 6.10 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
# title		Other operating systems:
# root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
# title		Microsoft Windows XP Professional
# root		(hd0,0)
# savedefault
# chainloader	+1

---

### Post by entangled on 2007-02-10
Only one other suggestion. 
Your laptop keyboard is OK, but only after booting. Can you get into your BIOS using the laptop keyboard just after switch on? Probably an F2 or F10 or ...
If you can then the keyboard hardware is actually recognized by the BIOS firmware and it is only grub that is having the problem. I suggest going to lilo ...:-|

---

### Post by entangled on 2007-02-10
> **Rich78 said:**
> USB keyboards don't work in GRUB.

Try using your actual laptop keyboard and you'll probably find it'll work.

My Intel mac mini only has bluetooth or USB peripherals. I've not had a problem yet using USB keyboard with grub.

---

### Post by Graham1 on 2007-02-10
> **entangled said:**
> Only one other suggestion. 
Your laptop keyboard is OK, but only after booting. Can you get into your BIOS using the laptop keyboard just after switch on? Probably an F2 or F10 or ...
If you can then the keyboard hardware is actually recognized by the BIOS firmware and it is only grub that is having the problem. I suggest going to lilo ...:-|

Thanks for your reply entangled :). The keyboard works fine in everything apart from the Grub menu :confused:. I don't understand why and I have even posted this problem on the HP forums but haven't had a reply :(. Anyhow, I have now re-installed openSUSE (as it loads automatically). Must be a problem with the laptop as it occurs in openSUSE 10.2 , Ubuntu 6.10 and Fedora Core 6.

:)

---

