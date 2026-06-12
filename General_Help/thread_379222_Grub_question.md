---
title: "Grub question"
date: 2007-03-08
forum: General Help
---

### Post by carverj on 2007-03-08
Hi there gang,
                          I have installed Ubuntu on the sda2 of my primary drive and my slave was added to the grub menu. Now I want to remove the slave in order to insert my older slave drive to gather data from it.
Only the windows boot option works from the list of partitions in grub. Any ideas why sda2 is unmountable (grub error 15 from memory ) in this senario?
Do I need to edit menu.list ?
Thanks and if this question doesn't make sense please reply so I may clarify
: )

---

### Post by sbassett on 2007-03-08
Can you slap you menu.lst file contents up here?

---

### Post by carverj on 2007-03-08
sure
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
# kopt=root=UUID=4c9f901f-cfdd-45b7-8e23-29a44834c08a ro
# kopt_2_6=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

#title		Ubuntu, kernel 2.6.17-11-generic
#root		(hd1,1)
#kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda2 ro quiet splash
#initrd		/boot/initrd.img-2.6.17-11-generic
#quiet
#savedefault
#boot

#title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
#root		(hd1,1)
#kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda2 ro single
#initrd		/boot/initrd.img-2.6.17-11-generic
#boot

title		Ubuntu, kernel 2.6.17-10-386
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.17-10-generic (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.17-10-generic (recovery mode) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, memtest86+ (on /dev/hda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.17-10-generic (on /dev/sda2) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.17-10-generic (recovery mode) (on /dev/sda2) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, memtest86+ (on /dev/sda2) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

I don't understand why the entry for sda2 would no longer mount if a slave disk is removed
Thanks for the reply also

---

### Post by bernied on 2007-03-08
You've got two sets of entries there, one to each of two disks (hd1) and (hd0). Look at the 'root' lines.
Your boot menu must be a nightmare. I lost count at 10 entries. 

So
- are your windows and ubuntu installs on the same disk?
- which windows entry boots, the one in the middle, or the one at the bottom?
- are you sure you've tried all of those ubuntu entries. Do you get the same error message for all of them?

[This](http://users.bigpond.net.au/hermanzone/) is a good place to start with multi-booting.

---

### Post by carverj on 2007-03-08
> You've got two sets of entries there, one to each of two disks (hd1) and (hd0). Look at the 'root' lines.
Your boot menu must be a nightmare. I lost count at 10 entries. 

So
- are your windows and ubuntu installs on the same disk?
- which windows entry boots, the one in the middle, or the one at the bottom?
- are you sure you've tried all of those ubuntu entries. Do you get the same error message for all of them?

This is a good place to start with multi-booting

hmm, yes, i didn't notice that. This is the entry I am trying to boot from as it is the entry that works before I remove the slave. And yes i tried to boot from all the other entries without success

```
title		Ubuntu, kernel 2.6.17-10-386
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot

```

root says hd 1,1 here which means grub thought the primary was the slave?. So if I were to change it to hd0,1, could I then boot in?

---

### Post by bernied on 2007-03-08
> **carverj said:**
> root says hd 1,1 here which means grub thought the primary was the slave?. So if I were to change it to hd0,1, could I then boot in?
You won't do any harm trying. But you already have some entries pointing at that partition, what happens when you try to boot the one that is below the first windows entry?

Does it give you the same error message as the first ubuntu entry?

Are windows and ubuntu on the same disk?

Which windows entry works?

Grub sees disks differently to linux, so just because linux sees the disk as first, doesn't mean grub will. I don't think grub has had much upgrading recently, and I think sata disks mixed with ide confuse the poor wee thing.

---

### Post by carverj on 2007-03-08
> You won't do any harm trying.
Yes, will try later, I should be doing a report now. oops, Ubuntu is to much fun


>  But you already have some entries pointing at that partition 
Yes, there are a couple of entries pointing to hd1,1, one is jsut the original or generic header yeah? 

> , what happens when you try to boot the one that is below the first windows entry?Does it give you the same error message as the first ubuntu entry?

The (hd0,1) entry below the first windows booted into slave but would not make it to login, perhaps as it is configured for a different machine.. I seem to have problems booting into my old computers drives/partitions, but thankfully am able to mount from master, and mount for data extraction

> 
Are windows and ubuntu on the same disk?

master has vista and ubuntu partition
slave has XP and ubuntu

> 
Which windows entry works?

I only tried the first (hd0,0) and it works fine regardless of which slave is installed
I didn't actually notice the final entry: 
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```
This looks like it is saying, boot into Vista regardless of master or slave. Perhaps this code will work for the  IDE/SATA problem that is affecting Ubuntu boot.
Such as, 
```
title		Ubuntu, kernel 2.6.17-10-386
root		(hd1,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

``` 
Is this the solution?
> 
Grub sees disks differently to linux, so just because linux sees the disk as first, doesn't mean grub will. I don't think grub has had much upgrading recently, and I think sata disks mixed with ide confuse the poor wee thing.

Aye, ken
hehe, love Edinburgh

---

### Post by bernied on 2007-03-08
The solution might be as simple as changing the (hd1,1) for (hd0,1), like this:
```
title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot
```

I'm actually australian, but it's a long story. I lived in Brisvegas for 10 years or so.

---

### Post by carverj on 2007-03-08
Born in B-vegas
Lived in Edinburgh/Donaghadee(N.Ireland) 2 years.
Enjoy all that snow eh!
oh, and thanks for all your help!!

---

