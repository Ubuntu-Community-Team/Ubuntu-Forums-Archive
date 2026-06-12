---
title: "Too many in Grub?"
date: 2007-07-21
forum: General Help
---

### Post by nick.inspiron6400 on 2007-07-21
I had dual-booting Ubuntu and Winblows XP, I added Kubuntu and everything seems to work fine. But on the Grub loader I seem to have many options, some with differenet kernels etc etc. I would like to know what is the same way to change this. 

I checked the menu.lst and this is what i have:

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=927c0a74-e114-4b3a-9bd6-6e4380f4a6bb ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=927c0a74-e114-4b3a-9bd6-6e4380f4a6bb ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.20-16-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e07f807d-f677-4425-a13b-1a27c58ef38a ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e07f807d-f677-4425-a13b-1a27c58ef38a ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.20-15-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e07f807d-f677-4425-a13b-1a27c58ef38a ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e07f807d-f677-4425-a13b-1a27c58ef38a ro single 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, memtest86+ (on /dev/sda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

If you could please tell me how to edit this, and how to save it. 

Thank you,

Nick.

---

### Post by n00bWillingToLearn on 2007-07-21
```
 gksudo gedit /boot/grub/menu.lst 
```

Use that command to edit your menu.lst, there should be an area like this 
```
 ## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all
``` 

*without uncommenting it* change howmany=all to howmany=< the number of kernels you wish to be shown at the grub menu> I have it set to #howmany=2 for instance so that if something goes wrong with a kernel upgrade I can still choose the older kernel that was working, but at the same time the menu is not cluttered with kernels from years ago. Note that you actually get two menu items per kernel, one of them to boot normally and another for recovery mode. Once you have that set how you like run:
```
 sudo update-grub 
``` in a terminal to update the rest of your menu.lst to match the change.

---

### Post by nick.inspiron6400 on 2007-07-21
Thank you for your reply, I followed your advice. I changed it to 1 and I still have both kernels, what can I do?

Thanks,

Nick.

---

### Post by davidjmayo on 2007-07-21
> **nick.inspiron6400 said:**
> Thank you for your reply, I followed your advice. I changed it to 1 and I still have both kernels, what can I do?

Thanks,

Nick.

In your menu.lst comment out  the one(s) you dont want with # at the start of the line

---

### Post by nick.inspiron6400 on 2007-07-22
Thanks!

I will put a # by the ones i don't want.

---

### Post by nick.inspiron6400 on 2007-07-22
I don't have them anymore listed in menu.lst. But when I boot I see them??

Help!

Nick.

---

### Post by davidjmayo on 2007-07-22
sorry Nick I forgot step 2

```
sudo update-grub
```

---

### Post by nick.inspiron6400 on 2007-07-22
I will give it a go, Also do I just put the # at the beginning? Or anywhere else.

So where it says "title" i just put a # before it?

Thank you.

---

### Post by davidjmayo on 2007-07-22
backup grub menu first

```
cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
``` 

Not just title the whole section

> title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4e54cfb6-00fd-472b-9ea6-808a8b05d1c5 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault


change to
> 
# title		Ubuntu, kernel 2.6.20-15-generic
# root		(hd0,1)
#  kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4e54cfb6-00fd-472b-9ea6-808a8b05d1c5 ro #  quiet splash
# initrd		/boot/initrd.img-2.6.20-15-generic
# quiet
# savedefault

---

### Post by kirios on 2007-07-22
[COLOR="DarkRed"]Change 'all' to '1' in the last line of this section: [/COLOR]

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

[COLOR="DarkRed"]Change 'true' to 'false' in the last line of these sections (but DO NOT UNCOMMENT THEM):[/COLOR] 

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true 

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

[COLOR="DarkRed"]Comment out the following by adding a # at the start of each line[/COLOR]

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/sda2)
root (hd0,1)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=e07f807d-f677-4425-a13b-1a27c58ef38a ro single
initrd /boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title Ubuntu, kernel 2.6.20-15-generic (on /dev/sda2)
root (hd0,1)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=e07f807d-f677-4425-a13b-1a27c58ef38a ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/sda2)
root (hd0,1)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=e07f807d-f677-4425-a13b-1a27c58ef38a ro single
initrd /boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title Ubuntu, memtest86+ (on /dev/sda2)
root (hd0,1)
kernel /boot/memtest86+.bin
savedefault
boot

[COLOR="DarkRed"]At this point, the only uncommented options you should have are:[/COLOR] 

title Ubuntu, kernel 2.6.20-15-generic
root (hd0,3)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=927c0a74-e114-4b3a-9bd6-6e4380f4a6bb ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault 

title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1

title Ubuntu, kernel 2.6.20-16-generic (on /dev/sda2)
root (hd0,1)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=e07f807d-f677-4425-a13b-1a27c58ef38a ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
savedefault
boot

[COLOR="DarkRed"]Finally, run **sudo update-grub**[/COLOR]

---

### Post by nick.inspiron6400 on 2007-07-22
I have tried all your advice, and it still is there!!!!

I am really tired of this, In Kubuntu I get all the options, but I can't save it. Something to do with permissions,

In Ubuntu I only get Ubuntu, I have edited the file, then did sudo update-grub. And it still is there.

Please help!

Nick.

---

### Post by nick.inspiron6400 on 2007-07-22
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
# kopt=root=UUID=927c0a74-e114-4b3a-9bd6-6e4380f4a6bb ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=false

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
# howmany=1

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=927c0a74-e114-4b3a-9bd6-6e4380f4a6bb ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=927c0a74-e114-4b3a-9bd6-6e4380f4a6bb ro single
initrd		/boot/initrd.img-2.6.20-16-generic

#title		Ubuntu, kernel 2.6.20-15-generic
#root		(hd0,3)
#kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=927c0a74-e114-4b3a-9bd6-6e4380f4a6bb ro quiet splash
#initrd		/boot/initrd.img-2.6.20-15-generic
#quiet
#savedefault

#title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
#root		(hd0,3)
#kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=927c0a74-e114-4b3a-9bd6-6e4380f4a6bb ro single
#initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.20-16-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e07f807d-f677-4425-a13b-1a27c58ef38a ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e07f807d-f677-4425-a13b-1a27c58ef38a ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
#title		Ubuntu, kernel 2.6.20-15-generic (on /dev/sda2)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e07f807d-f677-4425-a13b-1a27c58ef38a ro quiet splash 
#initrd		/boot/initrd.img-2.6.20-15-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
#title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/sda2)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e07f807d-f677-4425-a13b-1a27c58ef38a ro single 
#initrd		/boot/initrd.img-2.6.20-15-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, memtest86+ (on /dev/sda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot


Than i try to save it, and I get this message:

The document could not be saved, as it was not possible to write to file:///boot/grub/menu.lst.
Check that you have write access to this file or that enough disk space is available.

---

### Post by kirios on 2007-07-23
[COLOR="DarkRed"]You need root privileges to save the changes. Use one of the following commands to open the file: [/COLOR]
**gksudo gedit /boot/grub/menu.lst **(in Ubuntu)
**kdesu kate /boot/grub/menu.lst** (in Kubuntu) 
[COLOR="DarkRed"]Now you'll be able to overwrite the previous version.[/COLOR]

---

### Post by nick.inspiron6400 on 2007-07-23
THANK YOU.

I have sorted it all out, Thank you guys for all your help.

Nick.

---

