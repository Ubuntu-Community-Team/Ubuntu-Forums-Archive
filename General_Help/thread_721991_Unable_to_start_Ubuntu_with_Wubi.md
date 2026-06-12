---
title: "Unable to start Ubuntu with Wubi"
date: 2008-03-11
forum: General Help
---

### Post by svenofix on 2008-03-11
I am not completely sure that this problem is related to Wubi, but I find it most likely that it is.

I recently installed Wubi and had Ubuntu 7.04 installed. However when I reboot my computer, 
and tried to load Ubuntu from the OS selection page (GRUB I believe its called), 
Ubuntu loads up until this point and freezes:

[FONT="Courier New"] 
Booting 'Ubuntu'

(hd0,2)
Filesystem type is NTSF, partition type 0x7.
    [Linux-bz Image, setup=0x1c00, size=0x1a82cc]
[/FONT]

It doesn't load beyond this point. Is there something that I have to do beforehand?
Or am I doing something wrong? I do know that there is something wrong with my memory 
(I ran a diagnostics test, but can't remember the memory related error that I got).

My computer, or rather laptop is an:
[FONT="Courier New"]Inspiron 6400
Intel T2250 1.73GHz
504MB RAM[/FONT]

---

### Post by ago on 2008-03-12
Can you please try wubi 8.04?

[http://wubi-installer.org/devel/minefield](http://wubi-installer.org/devel/minefield)

---

### Post by svenofix on 2008-03-12
Wubi 8.04 was the one that I used. However after some experimenting,
 I figured out how to start Ubuntu. Kind of annoying though. I have to
 have my boot order boot up my cdrom drive then my hard drive,
and I have to when press F12 right when my laptop is starting up and
select boot from hard drive. This is the only way I can get Ubuntu up
and running. I don't why, not to mention it doesn't make sense.:confused:

---

### Post by ago on 2008-03-12
How many hard disks do you have? 
Where is wubi installed?
What is in /ubuntu/disks/boot/grub/menu.lst?

---

### Post by svenofix on 2008-03-15
I have 1 hard disk and two partitions. Wubi is installed in the second one
(the Backup storage for Dell, I believe).

As for menu.lst:


```
[FONT="Courier New"]# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=find=/wubi/boot/linux ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=find --set-root --ignore-floppies /wubi/boot/linux

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

title		Ubuntu, kernel 2.6.20-15-generic
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/wubi/boot/vmlinuz-2.6.20-15-generic find=/wubi/boot/linux ro quiet splash
initrd		/wubi/boot/initrd.img-2.6.20-15-generic
boot

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/wubi/boot/vmlinuz-2.6.20-15-generic find=/wubi/boot/linux ro single
initrd		/wubi/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title Ubuntu (Original Kernel)
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux setup_iso=ubuntu-7.04-alternate-i386.iso quiet splash ro
initrd /wubi/boot/initrd
boot[/FONT]

```
I have hardly any clue as to what any of that means.
As an edit to my last post, I don't need to have my boot order boot the cd-rom first. 
I just happen to get into Ubuntu and seemingly
random times. It also occurs to me that when trying out Wubi I had 
downloaded it twice, because I thought it got stuck with downloading
Ubuntu. Maybe that's wherein my problem lies. I also have noticed
that there are two places where the files [FONT="Courier New"]wubildr[/FONT] and [FONT="Courier New"]wubildr.mbr[/FONT]
are installed (one in my C: drive, the other in the Wubi install drive).

Hope that's not too much information at once, and hope it helps.

---

### Post by ago on 2008-03-16
DId you complete the installation? If so the relevant menu.lst is the one in /ubuntu/disks/boot/grub/menu.lst

---

### Post by svenofix on 2008-03-16
Ya, I did complete the installation with the first download of Wubi.
Is the [FONT="Courier New"]menu.lst[/FONT] file in Windows or Ubuntu?
Since I got it out of Ubuntu (I am able to get on, but with trouble).

---

### Post by ago on 2008-03-16
In windows it is under /ubuntu/disks/boot/grub/menu.lst
In ubuntu it is under /boot/grub

but it is the same file

---

### Post by svenofix on 2008-03-18
**How** do I know whether or not it's the relevant [FONT="Courier New"]menu.lst[/FONT] file or not? And if it is, then what?

---

### Post by ago on 2008-03-19
[http://ubuntuforums.org/showpost.php?p=4541576&postcount=45](http://ubuntuforums.org/showpost.php?p=4541576&postcount=45)

---

### Post by svenofix on 2008-03-19
I think that fixed my problem!

Thanks for all the help! :p

---

