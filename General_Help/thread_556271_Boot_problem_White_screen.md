---
title: "Boot problem White screen??"
date: 2007-09-21
forum: General Help
---

### Post by hagarid on 2007-09-21
OK I am kind of a novice here so be gentle. My problem is when I boot I get a white screen I hear all the beeps and flickers as if the computer is booting normally, but can see nothing but white. I unplug the computer and restart 3 or four times and eventully I see all the boot up stuff I am suppose to see and everything is fine again. Not sure what is going on here. I am running a dual boot Vista home Prem & Ubuntu box. I have a Nvidia 6200 A-LE video card. I have an HP pavilion a520n. I added the video card and 256 more ram to give me 786 now.  everything else is stock. I know this setup works It was fine for about the last 6 months or so and even survived me upgrading to Fiesty Fawn from the older version. Not really sure when or what happened all of the sudden this boot problem started. I have tried to reinstall Ubuntu to get rid of it but to no avail. I attached a copy of the boot menu to see if it is there and have use Envy from [http://www.albertomilone.com/nvidia_scripts1.htm](http://www.albertomilone.com/nvidia_scripts1.htm) to install the video card. I don't think I did anything when I installed the Ram though. OK I hope that is enough info for you guys to see exactly what I did wrong and laugh alot. But if not let me know and I will send more. Thanks in advance

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
# kopt=root=UUID=2ba8b56d-598a-44e3-ba7d-55e05c29c6a7 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2ba8b56d-598a-44e3-ba7d-55e05c29c6a7 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2ba8b56d-598a-44e3-ba7d-55e05c29c6a7 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, memtest86+
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
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by DamjanDimitrioski on 2007-09-21
I had the same problem with my nvidia ge force card.
When you install drivers for nvidia or reconfigurating the card with dpkg-reconfigure -phigh xserver-xorg don't forget to uncheck first the 3d acceleration in the resitricted drivers.
Cause if you open an program or game which requers opengl 3d accel. the whole screen will be white.
For instance you have beryl-manager put in session to startup with the login, but if you reinstalled the driver, on the next boot the computer will stuck with one color or whatever it is called.
This counts only for ati and nvidia.
I recomends You to buy a none ati or nvidia card, or to uncheck the accel. in restricted manager each time you install new drivers.

If you didn't understand or this not what you asking for, please send a reply, bye!

P.S> Good luck!

---

### Post by hagarid on 2007-09-21
Well. I guess I didn't explain right. see I have had this installed for about 3 or 4 months and just recently it has started happening. I uninstalled and reinstalled everything then just Ubuntu but it still happens I think there is something else I missed.

---

