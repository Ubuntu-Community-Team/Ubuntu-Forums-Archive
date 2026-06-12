---
title: "Ubuntu wont boot up!"
date: 2007-12-20
forum: General Help
---

### Post by diwas on 2007-12-20
kernel panic - not syncing: No init found. Try passing init=option to kernel.

This error comes up whenever i boot up Gutsy. Actually i had some series of interrupted shutdown. I did shutdown ubuntu just by pulling the plug several times. Now this message pops in whenever i boot up my gutsy.
Does anyone have the solution? Please dont say to format my drive and install again...i have lots of settings in it which i dont want to loose...lots of dependency files are also download...i dont want to re-download them all.

Thank you.

---

### Post by timseal on 2007-12-20
Boot from a live cd and run fsck on the drive.

---

### Post by diwas on 2007-12-21
what will this command do? isnt this for checkin the file system?
and are you talkin abt the root drive in which ubuntu is installed?

---

### Post by t-bone510 on 2007-12-21
fsck = file system check


it will check for errors and fix them if possible

---

### Post by timseal on 2007-12-21
Yes, and yes.
You pulled the plug several times, which probably corrupted the filesystem a bit. Or a lot.   If you have more than one partition, run fsck on each one.

Oh, and when you find yourself asking > what will this command do?  you can try man <whatever> or google it.  You'll get a better answer that way.

---

### Post by t-bone510 on 2007-12-21
Never, ever, pull the plug like that.

Linux seems to have a more sensitive filesystem than Windows.

Here is what you do

If you experience a lockup, and no keys/mouse movements have an effect, push these keys, it has saved me many times..

   1. Hold down the Alt and SysRq (Print Screen) keys.
   2. While holding those down, type the following in order. Nothing will appear to happen until the last letter is pressed: REISUB
   3. Watch your computer reboot magically.

R gives back control of the keyboard
S issues a sync
E sends all processes but init the term singal
I sends all processes but init the kill signal
U mounts all filesystem ro to prevent a fsck at reboot
B reboots the system


What this basically does is terminate all processes, save what can be saved, and reboot without owning the filesystem

---

### Post by diwas on 2007-12-21
hmm thank you.
But i have checked this...nothing happens...i mean no change while booting.

---

### Post by t-bone510 on 2007-12-21
I have no idea what you just said.. sorry. :(

---

### Post by diwas on 2007-12-21
Hehe..i meant the fsck thing. I had done that earlier...but it wont help in bootin up..kernel panic still shows in.

---

### Post by timseal on 2007-12-21
can you post your /boot/grub/menu.lst file?

---

### Post by diwas on 2007-12-22
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
default		4

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
# kopt=root=UUID=4a4c7b6a-3cc5-441a-875e-f99bcfd3b48e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4a4c7b6a-3cc5-441a-875e-f99bcfd3b48e ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4a4c7b6a-3cc5-441a-875e-f99bcfd3b48e ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by (((X))) on 2007-12-28
If you are not able to boot Ubuntu try to edit partitons in grub menu, on grubmenu press e or so to edit partition parameters. You can also edit /boot/grub/menu.lst to always boot the way you want.

change

title Ubuntu 7.10, kernel 2.6.22-14-generic
 root (hd0,5)
 kernel /boot/vmlinuz-2.6.22-14-generic root=[COLOR="DarkOrchid"]UUID=4a4c7b6a-3cc5-441a-875e-f99bcfd3b48e[/COLOR] ro quiet splash
 initrd /boot/initrd.img-2.6.22-14-generic

to

title Ubuntu 7.10, kernel 2.6.22-14-generic
 root (hd0,5)
 kernel /boot/vmlinuz-2.6.22-14-generic root=[COLOR="YellowGreen"]/dev/sda?yourpartition[/COLOR] ro quiet splash
 initrd /boot/initrd.img-2.6.22-14-generic

Your menu.lst is too long, this is how mine looks like:
___________________________________________________________
timeout 15
color cyan/blue white/blue
foreground ffffff
background 2f5178
gfxmenu /boot/grub/message

title MEPIS32 at sda1, newest kernel
root (hd0,0)
kernel /boot/vmlinuz root=/dev/sda2 nomce quiet vga=791 
boot

title Run MEMTEST to test system memory
kernel /boot/memtest86+.bin

___________________________________________________________

---

### Post by diwas on 2007-12-31
Thank you.
I will do as you have said, hope it works!
And how is this possible, your menu.lst is so small...??

---

### Post by (((X))) on 2008-01-02
jeah, but after sudo update-grub, it adds more lines in menu.lst..

---

### Post by diwas on 2008-01-03
I have (after trying for 3 weeks) escaped the problem...but again a new problem has arised...i have a dial up modem and no alternative...last time i searched for the modem driver for abt 6mnths with other computer and finally i found it out. I installed it and Voilla...it worked. Today i reinstalled Ubuntu and tried to install the driver...but the same driver wont work this time. Gosh...this is again a new headache for me...damn...anyone know what might be the appropriate solution??

---

