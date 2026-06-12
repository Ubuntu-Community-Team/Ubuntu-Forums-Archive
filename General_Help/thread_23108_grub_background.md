---
title: "grub background"
date: 2005-03-31
forum: General Help
---

### Post by Michael on 2005-03-31
Hi.
I have followed the "Instructions for Installing a Custom GRUB Background" in [Ubuntu Artwork Wikipage](http://www.ubuntulinux.org/wiki/UbuntuArtwork).

I added this line to my menu.lst:
```
splashimage=(hd0,0)/boot/grub/ubuntu.xpm.gz
```
(downloaded from [here](http://www.schultz-net.dk/grub.html))
but when I boot my pc all I see is a black screen with a blinking caret in the top-left corner of the screen. GRUB *is* working (I remeber the order of the selections so I can choose winxp/ubuntu blindly) but it shows nothing at all.

What can be the problem?

menu.lst:
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## l33t gr4ph1x
splashimage=(hd0,0)/boot/grub/ubuntu.xpm.gz

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
# savedefault
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/sda5 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu Linux 5.04
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.10-5-686-smp root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-686-smp
savedefault
boot

title		Ubuntu Linux 5.04 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.10-5-686-smp root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.10-5-686-smp
savedefault
boot

title		memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


```

EDIT: lol omg I'm so dumb... I added the wrong line, silly me. Restarting now with correct line.

EDIT2: Now it is correct, but still does not work!

EDIT3: Third time ice cream I guess because I solved the error: I changed (hd0,0) to (hd0,4) (where my linux / partition is) and now it, obviously, works.

Guess I should look more carefully next time, thank you for your support :p

---

### Post by lao_V on 2005-03-31
Doesn't it feel great when you solve an issue yourself? :-) Welcome to the insomniac world of linux :-)

---

### Post by arctic on 2005-03-31
hmm... i remember that i experienced something similar when setting up my cuadruple boot system, forgetting to change the hdx.x to the correct values in grub after using lilo for ages. i spent two days on that idiotic thing. :D

---

### Post by bored2k on 2005-03-31
I use grubconf for this , its delicate and with a good gui its so easy to set up ^_^ .

---

