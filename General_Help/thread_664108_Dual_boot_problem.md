---
title: "Dual boot problem"
date: 2008-01-10
forum: General Help
---

### Post by chadikins on 2008-01-10
I am a linux newbie. I have 2 sata hd's. The plan was to boot new drive with Ubuntu 6.06 and leave the original untouched with Win XP. I did a practice installation with the XP drive unplugged. Everything was fine. Then I plugged it back in and reinstalled. Everything went ok. But when the GRUB menu comes up on reboot, I cant choose any OS's. It says "error 17 - cannot mount selected partition". I rebooted again, this time before it made it to the GRUB screen I got a message that said Error 21, and that was all. Please help. I can't even get my windows drive to boot. I didn't do anything to it, so I figure there must be a way to fix it, somehow involving the GRUB. I wanted to keep linux as another system, but so far I am freaking out about it.
Please help!

---

### Post by logos34 on 2008-01-11
Sounds like maybe grub installed to the MBR of the XP drive the second time around. Are you perhaps still booting from the ubuntu drive?  Go into the Bios and switch the hard disk boot order.

---

### Post by ubu-for on 2008-01-11
> **chadikins said:**
> I am a linux newbie. I have 2 sata hd's. The plan was to boot new drive with Ubuntu 6.06 and leave the original untouched with Win XP. I did a practice installation with the XP drive unplugged. Everything was fine.

Ok.

> **chadikins said:**
> Then I plugged it back in and reinstalled.

And reinstalled what?

Here is my "device.map" and "menu.lst" from "/boot/grub".

**device.map**
```
(hd0)	/dev/sda
(hd1)	/dev/sdb

```

**menu.lst** with "Windows XP C:\" on disk1 partition1 and "Ubuntu root" on disk1 partition4
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
timeout		5

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
# kopt=root=UUID=b7133745-3bcb-445f-863b-af49bbd3f9b8 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
# howmany=2

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=b7133745-3bcb-445f-863b-af49bbd3f9b8 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=b7133745-3bcb-445f-863b-af49bbd3f9b8 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b7133745-3bcb-445f-863b-af49bbd3f9b8 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b7133745-3bcb-445f-863b-af49bbd3f9b8 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Maybe [this HOWTO](http://www.google.com/translate?u=http%3A%2F%2Fwiki.ubuntuusers.de%2FGRUB%3Faction%3Dshow%26redirect%3DGrub&langpair=de%7Cen&hl=en&ie=UTF8) translated by Google can help to solve your problem.

---

### Post by chadikins on 2008-01-11
Thanks. I rebooted again and in the bios changed something, but it was the same thing I had done before, only this time it worked. Not sure I understand. I understand how it is suposed to work, but not sure why I had problems. A question- if I have XP and linux (which has GRUB) and I set XP to boot first, doesn't linux still technically boot first because of GRUB? Also, how do I access the GRUB terminal?
By reinstalled, I meant I reinstalled ubuntu with both drives plugged in instead of having the XP drive unplugged. 
Thanks, I really appreciate it!

---

### Post by jken146 on 2008-01-11
Ubuntu doesn't boot, but GRUB (which is a bootloader) does run.  It uses a file on your Ubuntu hard disk, /boot/grub/menu.lst to get its configuration.  If you choose to boot to windows from GRUB, you are just passed on to the Windows bootloader and Windows boots.

---

### Post by ubu-for on 2008-01-11
> **chadikins said:**
> A question- if I have XP and linux (which has GRUB) and I set XP to boot first, doesn't linux still technically boot first because of GRUB?

I'm not a Linux Pro but I think GRUB boots first and is not dependent on your Linux distribution (Ubuntu).

1. BIOS boots your HDDs with GRUB
2. GRUB boots whatever stands in your "menu.lst"

> **chadikins said:**
> Also, how do I access the GRUB terminal?

When GRUB loads, press "ESC".

BTW You can turn on the GRUB boot menu and change the timeout by editing the "menu.lst".

**OLD**

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
```

**NEW**

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		60

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```

> **chadikins said:**
> Thanks, I really appreciate it!

You're welcome!

---

