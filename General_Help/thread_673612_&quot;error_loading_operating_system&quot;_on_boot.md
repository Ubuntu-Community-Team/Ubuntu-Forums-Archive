---
title: "&quot;error loading operating system&quot; on boot"
date: 2008-01-20
forum: General Help
---

### Post by NoSmokingBandit on 2008-01-20
I had a working Gusty/xp dual boot going on yesterday but i had to reinstall xp (my own fault, really). So i went through and got windows all squared away then set my ubuntu partition active so i could boot with grub but now i get the "Error Loading Operating System" message before grub even shows up. I can boot into xp if i set that partition active but i cant seem to get ubuntu to load now.
I heard that it could be a menu/lst problem but i didnt see anything wrong in it:
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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		3

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color white/blue white/black

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=17b143d4-6e60-47b1-a5a9-5f80644ca8da ro

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
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=17b143d4-6e60-47b1-a5a9-5f80644ca8da ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=17b143d4-6e60-47b1-a5a9-5f80644ca8da ro single
initrd		/boot/initrd.img-2.6.22-14-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Microsoft Windows XP Professional
root		(hd0,2)
savedefault
makeactive
chainloader	+1


```
I have ubuntu on the first partition, then the swap, then XP on the third partition, then a 4th partition for storage and stuff. Anyone know what went wrong?

---

### Post by sumguy231 on 2008-01-20
I don't see anything wrong with that menu.lst but you could try reinstalling GRUB fresh using the Super Grub Disk:
[http://forjamari.linex.org/projects/supergrub/](http://forjamari.linex.org/projects/supergrub/)

---

### Post by NoSmokingBandit on 2008-01-21
i made the disk but when i boot from it i get the message:

Remove disks and other media
Press any key to reboot.

So i do that and after i press a button it doesnt reboot but just spits out the "error loading operating system" error again.

---

### Post by NoSmokingBandit on 2008-01-22
Anyone? I'd really like to use ubuntu again :/

---

### Post by dreblen on 2008-01-22
I'm pretty sure that installing windows after linux will wipe the linux installation, so reinstalling xp probably killed ubuntu (or at least the boot record). Try running a live cd to see if there is anything on your linux partition, and if there is, you might want to make a backup and then reinstall ubuntu

---

### Post by NoSmokingBandit on 2008-01-22
all the files are still there. So that kinda sucks. I hate reinstalling, but i've done it enough with ubuntu by now i should be a pro.
Anyway, for the most part i only use my linux partition for video encoding. Is there a way to set up ubuntu to do this uber-fast or is there a distro that is generally really fast at this kind of stuff? I dont care about looks (although i do prefer a gui over command line). Or should i take this to the multimedia section of the forums?

---

### Post by dreblen on 2008-01-22
I don't personally use it so I can't say if it's good or bad for video encoding, but have you checked out Ubuntu Studio? [http://ubuntustudio.org/](http://ubuntustudio.org/)

---

