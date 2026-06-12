---
title: "help boot iso from grub??"
date: 2008-05-18
forum: General Help
---

### Post by mjp216 on 2008-05-18
ok, i want to boot an ISO image in grub so i can install windows... i know, i know, windows sucks... i am aware of this, its just something i must do, i will be re-installing ubuntu. so please, dont ask why i am doing this, i just need help.

i made a new partition (/dev/sda2), i formatted it to FAT32, mounted it (/media/disk), and i put the ISO on it.

I dont know how to get GRUB to boot it. i looked in my /boot/grub/menu.lst
and it is rediculous, i have too much on their, and i dont want to mess it up, so i need help, and ill post my menu.lst below.

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
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
# kopt=root=UUID=5087dbce-20ad-49d2-b747-ff7fa60999cd ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

title		Ubuntu 8.04, kernel 2.6.24-17-rt
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-17-rt root=UUID=5087dbce-20ad-49d2-b747-ff7fa60999cd ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-rt
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-rt (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-17-rt root=UUID=5087dbce-20ad-49d2-b747-ff7fa60999cd ro single
initrd		/boot/initrd.img-2.6.24-17-rt

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=5087dbce-20ad-49d2-b747-ff7fa60999cd ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=5087dbce-20ad-49d2-b747-ff7fa60999cd ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-rt
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-rt root=UUID=5087dbce-20ad-49d2-b747-ff7fa60999cd ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-rt
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-rt (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-rt root=UUID=5087dbce-20ad-49d2-b747-ff7fa60999cd ro single
initrd		/boot/initrd.img-2.6.24-16-rt

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5087dbce-20ad-49d2-b747-ff7fa60999cd ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5087dbce-20ad-49d2-b747-ff7fa60999cd ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.24-15-rt
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-15-rt root=UUID=5087dbce-20ad-49d2-b747-ff7fa60999cd ro quiet splash
initrd		/boot/initrd.img-2.6.24-15-rt
quiet

title		Ubuntu 8.04, kernel 2.6.24-15-rt (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-15-rt root=UUID=5087dbce-20ad-49d2-b747-ff7fa60999cd ro single
initrd		/boot/initrd.img-2.6.24-15-rt

title		Ubuntu 8.04, kernel 2.6.24-15-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=5087dbce-20ad-49d2-b747-ff7fa60999cd ro quiet splash
initrd		/boot/initrd.img-2.6.24-15-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-15-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=5087dbce-20ad-49d2-b747-ff7fa60999cd ro single
initrd		/boot/initrd.img-2.6.24-15-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5087dbce-20ad-49d2-b747-ff7fa60999cd ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5087dbce-20ad-49d2-b747-ff7fa60999cd ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
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
title		Windows Vista Home Premium
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


---

### Post by mjp216 on 2008-05-24
anybody, i really do need help with this??
somebody has to know.

---

### Post by aquavitae on 2008-07-17
I'm trying to do the same thing.  The closest I'm come while googling was a suggestion of creating a new cd format partition, writing the iso to it, then chainloading to it in grub.  But its not ideal and I don't know if it will work.

---

### Post by dracayr on 2008-07-17
?? why not simply burn the ISO to cd? GRUB can only boot partitions/HDDs, and it certainly can't mount ISOs...

dracayr

---

### Post by aquavitae on 2008-07-18
Its sometimes just a nuisance buring lots of cds when you're playing around with different distros.  And in my case its because I want to install a new distro onto an old laptop with a broken cd drive, and which won't boot from usb.  Grub can't mount iso's, but there should be a way to copy the contents of the iso to the hard drive and boot from it that way.  I tried that, copying the contents to /newcd and using this code in grub:
```
root (hd0,5)/newcd/
kernel /boot/vmlinuz-*<whatever the rest of it was, can't remember  now>*

```
And it started booting, but then I got a kernel panic. Unfortunately I had to go out then but I'm going to carry on trying later.  I think I need to add some arguments to the kernel command.

---

### Post by red_team316 on 2008-07-18
Why not use a VM?

---

### Post by aquavitae on 2008-07-18
How would that help?  I want to install it onto the hard drive, replacing the system I have at the moment.

---

### Post by bodhi.zazen on 2008-07-18
You can see if this thread helps :

[http://forums.whirlpool.net.au/forum-replies-archive.cfm/925285.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/925285.html)

See the last post.

---

### Post by jimv on 2008-07-18
I've never tried this, but I think you could use a partition as a virtual disk in VirtualBox, and then install XP from VirtualBox.

This guy has intructions on how to use an actual partition as a virtual disk:

[http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/](http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/)

---

### Post by Endolith on 2009-04-06
I'd like to know how to do this, too.  I'm not sure why Grub wouldn't be able to mount an ISO if it knew the location on the disk.  It has to understand file systems if it can access your menu.lst file, right?

Another possibility might be burning the ISO to a USB flash drive, using [http://unetbootin.sourceforge.net/?](http://unetbootin.sourceforge.net/?)

---

### Post by mysoogal on 2009-04-06
this is how i got things working pretty fine,

installed xp pro clean ! with all the updates 

next i downloaded Wubi - Ubuntu Installer for Windows
wubi-installer.org/

to start fresh it's better if you have 2 drives C:\ for Windows xp D:\for ubuntu

you will have double boot options to pick from xp or ubuntu everytime you reboot your computer.

so i can run xp in 1 mintue or run ubuntu the next mintue

if you want the virtual way, look up virtualbox or QUME something like that.

---

### Post by aquavitae on 2009-04-07
> **Endolith said:**
> I'd like to know how to do this, too.  I'm not sure why Grub wouldn't be able to mount an ISO if it knew the location on the disk.  It has to understand file systems if it can access your menu.lst file, right?

Another possibility might be burning the ISO to a USB flash drive, using [http://unetbootin.sourceforge.net/?](http://unetbootin.sourceforge.net/?)

Grub doesn't understand all file systems, and I think that iso9660 (the cd file system) is one that it doesn't.  I think I've found how to do it though, although it will still take a bit of research. As part of the boot process, grub loads a ram image containing a few drivers and programs required to boot the main system, e.g. obscure hard drive drivers.  It is possible to add anything to this image, such as filesystem drivers for iso images, the mount program and possibly a bootup script.  In my case I was trying to install arch linux, so I created an image which would load usb drivers, then boot off a flash drive.  You should be able to do something similar with an iso file.  In arch, the program used to create the image is called mkinitcpio (I think), and it would probably work in ubuntu too.

---

### Post by Endolith on 2009-04-07
> **aquavitae said:**
> Grub doesn't understand all file systems, and I think that iso9660 (the cd file system) is one that it doesn't.

Grub 0.95 added ISO9660 support.

Here's a better description:

> **[Booting from iso9660 images using GRUB 2]("http://www.mgerards.net/?p=16")**

                               In #grub one of the most asked questions is if GRUB can boot iso9660 images. Or better: how GRUB should do this, people don’t even think about if it would be possible or not. Of course this annoys many people and “GRUB can not boot CDROM images” is nowadays the most important line in the topic.

 Actually, GRUB can read ISO9660(”iso”) images. It can for example loads the first few sectors and boot it. But most people do not realize is “what then?”. What would the loaded operating system do? It will most likely look for a CDROM, which it won’t find and fail.
Also: [http://ubuntuforums.org/showthread.php?p=6930214](http://ubuntuforums.org/showthread.php?p=6930214)

It seems these LiveUSB things use ISOLINUX [http://en.wikipedia.org/wiki/Syslinux](http://en.wikipedia.org/wiki/Syslinux)

---

### Post by aquavitae on 2009-04-08
Interesting - I stand corrected!

---

