---
title: "Dual Boot?"
date: 2007-08-17
forum: General Help
---

### Post by cmillican on 2007-08-17
I just today booted off a liveCD of Kubuntu I have, partitioned out 10G of space for Windows XP (for my dad so he can use our extremely propreitary printer), installed a (less-than-legal) copy of XP, reinstalled GRUB, booted into my familiar Ubuntu, brought up GParted, right clicked the 10G partition, clicked manage flags, checked boot, and it unchecked my Ubuntu partition.

We now interrupt you to apologize for that long sentence.

Now I'm wondering how I can get both to be bootable. Isn't there a way to have an option at boot for which one I want?

Thanks for any advice,
Chris

---

### Post by Sef on 2007-08-17
When it comes up, it should give you an option to boot into the nondefault os.    If you do not change the os in 15 seconds (I think) then it will boot into the default os.

So what is the default?

Does it give you an option to change the os?

---

### Post by expatCM on 2007-08-17
Do both operating systems appear on the Grub menu list?

---

### Post by cmillican on 2007-08-17
No, only Ubuntu appears on the menu, and it gives me no option to boot another os.

---

### Post by guguma on 2007-08-17
First of all where did you install grub (I guess MBR)

There are two things possible to do about this. You can edit your grub.conf file, and add XP into it.

```
sudo gedit /boot/grub/grub.conf
```

You can post the contents here so that people can help.

Or you will use the windows cd to put NTLOADER to MBR and boot ubuntu using NTLOADER.

I suggest the first option, it is easier. Choose your option and let us help you.

---

### Post by cmillican on 2007-08-17
I decided I'd use the first option...weird thing is, there is no grub.conf in /boot/grub/...anybody know what that's about?

---

### Post by cmillican on 2007-08-17
There is a menu.lst file there...towards the bottom it has several entries like this
```

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=c634568b-dd20-49ae-ab66-aba6c3fcbd30 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault
```

---

### Post by guguma on 2007-08-17
sorry my mistake, menu.lst is the file. Now please post the whole file so that I will not mistakenly cause trouble for you, also please post where windows is installed (which partition of which hard drive).

---

### Post by cmillican on 2007-08-17
Windows is on (hd0,1)

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
# kopt=root=UUID=c634568b-dd20-49ae-ab66-aba6c3fcbd30 ro

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=c634568b-dd20-49ae-ab66-aba6c3fcbd30 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=c634568b-dd20-49ae-ab66-aba6c3fcbd30 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=c634568b-dd20-49ae-ab66-aba6c3fcbd30 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=c634568b-dd20-49ae-ab66-aba6c3fcbd30 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=c634568b-dd20-49ae-ab66-aba6c3fcbd30 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=c634568b-dd20-49ae-ab66-aba6c3fcbd30 ro single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=c634568b-dd20-49ae-ab66-aba6c3fcbd30 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=c634568b-dd20-49ae-ab66-aba6c3fcbd30 ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by guguma on 2007-08-17
Before doing anything backup this file.

Now at the end of the file add this and save the file.

```
title		Other operating systems:
root

title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
chainloader	+1
```

By the way you can consider cleaning that file a bit, removing early kernel boots and so.

Also please inform me if everything is O.K.

---

### Post by cmillican on 2007-08-17
Eww...it worked perfectly...I think I threw up a little in my mouth when the WinXP splash came up.

Thanks for all your help, man, that was really nice.

---

### Post by guguma on 2007-08-17
glad to be of help

---

