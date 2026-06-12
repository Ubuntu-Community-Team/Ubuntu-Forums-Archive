---
title: "Grub menu not showing additional entry"
date: 2006-12-18
forum: General Help
---

### Post by donniep152 on 2006-12-18
I'm trying to dual boot 2 hd's.  The first is Ubuntu  edgy my main distro and the second is PCLOS which is booting lilo.  Ubuntu is booting grub.  My menu.lst is below, but interesting enough, since I upgraded to the latest kernel, I can't even get the last entry for PCLOS to show up on my grub menu upon boot.  I'm sure it's something extremely simple, but I'm at wits end, being a somewhat newbie.  I had it working fine until the upgrade changed my grub and like a dummy did not have a copy of my old menu.lst   
It's very puzzling to me why it doesn't even show up on my grub boot.

Any help greatly appreciated!

here's my menu.lst

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
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=cb50c5f3-43a4-4a6a-9409-7d90b1ef731d ro
# kopt_2_6=root=/dev/hdb1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# defoptions=quiet splash vga=769

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
 # updatedefaultentry=true

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

Title		PCLOS
rootnoverify	(hd1,1)
Chainloader     +1
boot


### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by kairu0 on 2006-12-18
Have you done a "grub-install /dev/hda" since you added the entry?

---

### Post by donniep152 on 2006-12-18
Didn't know I had to.  Just ran it and got a "no errors"   upon reboot, still no entry for the PCLOS.

---

### Post by anaconda on 2006-12-18
It doesn't show because you dont have a line starting with 
title
in the last entry.

and no Title isn't the same than title. Big letters are completely different than small ones.
I think grub ignores lines that it can't understand.

---

### Post by donniep152 on 2006-12-18
Many thanks for the quick replies.  And, just as I thought, I missed something easy.  I don't care if it's Ubuntu, FC or PCLOS, the forums at all of these distros are the most helpful I've ever found.

Thanks Again,

---

