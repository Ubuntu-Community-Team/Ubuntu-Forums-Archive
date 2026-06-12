---
title: "Can't boot Windows XP anymore"
date: 2007-11-08
forum: General Help
---

### Post by Hank_61 on 2007-11-08
I'm running a dual boot between Gutsy and XP. In the past I've always just selected which OS I wanted to boot from after powering up my PC. But today when I went to go and do it, Windows XP wasn't an option on the list.

To be honest, I'm not sure when it stopped showing up on my list, because I almost never use Windows anymore. I'm wondering if maybe it disappeared after I upgraded from Feisty to Gutsy? I know the Windows partition hasn't been wiped out, because I can still access that partition from within Ubuntu, using the NTFS-3G driver. It's just that Windows won't show up on my boot list anymore. 

Does anyone know how I can get it back?


Here's my menu.lst...

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
# kopt=root=UUID=75583d51-845e-4ced-96fb-1a40cd0c9eef ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=75583d51-845e-4ced-96fb-1a40cd0c9eef ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=75583d51-845e-4ced-96fb-1a40cd0c9eef ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=75583d51-845e-4ced-96fb-1a40cd0c9eef ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=75583d51-845e-4ced-96fb-1a40cd0c9eef ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, kernel 2.6.17-12-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-12-generic root=UUID=75583d51-845e-4ced-96fb-1a40cd0c9eef ro quiet splash
initrd		/boot/initrd.img-2.6.17-12-generic
quiet

title		Ubuntu 7.10, kernel 2.6.17-12-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-12-generic root=UUID=75583d51-845e-4ced-96fb-1a40cd0c9eef ro single
initrd		/boot/initrd.img-2.6.17-12-generic

title		Ubuntu 7.10, kernel 2.6.17-11-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=75583d51-845e-4ced-96fb-1a40cd0c9eef ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet

title		Ubuntu 7.10, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=75583d51-845e-4ced-96fb-1a40cd0c9eef ro single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu 7.10, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=75583d51-845e-4ced-96fb-1a40cd0c9eef ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet

title		Ubuntu 7.10, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=75583d51-845e-4ced-96fb-1a40cd0c9eef ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

Not sure what to look for.

Any advice?

Thanks, 
Hank

---

### Post by HermanAB on 2007-11-08
Well, you are looking at the right file, but there is an amazing amount of crap in there.  What I would do, is backup that one and create a new menu.lst file from scratch.  If that file is longer than about 10 lines, then you are doing something wrong...

Cheers,

Herman

---

### Post by kellemes on 2007-11-08
> **Hank_61 said:**
> I'm running a dual boot between Gutsy and XP. In the past I've always just selected which OS I wanted to boot from after powering up my PC. But today when I went to go and do it, Windows XP wasn't an option on the list.

To be honest, I'm not sure when it stopped showing up on my list, because I almost never use Windows anymore. I'm wondering if maybe it disappeared after I upgraded from Feisty to Gutsy? I know the Windows partition hasn't been wiped out, because I can still access that partition from within Ubuntu, using the NTFS-3G driver. It's just that Windows won't show up on my boot list anymore. 

Does anyone know how I can get it back?


Here's my menu.lst...



Not sure what to look for.

Any advice?

Thanks, 
Hank

Well, to begin with you could comment-out all the kernellines you don't use.. so at least the menulist won't be so big.. Based on this menu.lst there should be at least one Windows-line in the bootmenu, working or not.

---

### Post by Maestro23 on 2007-11-08
Whats the output of:

> cat /etc/fstab

&

sudo fdisk -l

---

### Post by quantboy on 2007-11-12
This is a very annoying bug with Ubuntu 7.10.  How in the world did this get past Ubuntu QA?

Here's the fix:
[http://scriptlibrary.blogspot.com/](http://scriptlibrary.blogspot.com/)

---

### Post by quantboy on 2007-11-12
I believe there is a also a backup file of the menu.lst that you can also use to copy and paste the original windows grub entry.

---

