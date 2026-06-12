---
title: "Ubuntu, Kernel 2.6.20-16 Doesn't Boot!!!"
date: 2007-10-09
forum: General Help
---

### Post by jrharvey on 2007-10-09
After update my new kernal does not boot. After starting the computer It goes to Grub menu and then just goes blank. I can get into ubuntu by clicking on kernel 2.6.20-15 but I would like to either delete the new one or fix it. Would it work if I just removed it from synaptic package manager??? I want to be able to start a working kernel from default.

---

### Post by fjgaude on 2007-10-09
Without knowing more details of your setup let's just go into the boot menu and see what's there:

```
sudo gedit /boot/grub/menu.lst
```

Post the findings here, starting with ## ## End Default Options ## ## to the ending. Thanks.

---

### Post by jrharvey on 2007-10-09
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
# kopt=root=UUID=ebf53312-fd34-4fc6-adeb-5a8da1b85da4 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ebf53312-fd34-4fc6-adeb-5a8da1b85da4 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ebf53312-fd34-4fc6-adeb-5a8da1b85da4 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ebf53312-fd34-4fc6-adeb-5a8da1b85da4 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ebf53312-fd34-4fc6-adeb-5a8da1b85da4 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
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

### Post by fjgaude on 2007-10-09
Okay, very good.

Can't see anything wrong in menu.lst.

Go into /boot with file manager and see if the 2.6.20-16 files are there.

Say, did you ever try to start from the -16 recovery line?

---

### Post by jrharvey on 2007-10-09
Yes I did try recovery. The screen just goes completely dead after boot. Nothing comes up at all, just a blank screen. I saw that this issue was not uncommon but I couldn't find a fix for it. It looks like the files are there but I included a pic just in case you wanted to see.

---

### Post by fjgaude on 2007-10-09
Gosh, can't see any out of order there. It is beyond me what could be wrong. Maybe someone else can jump in here and help you get it going.

If you wish you could simply delete the entry for the -16 kernel in the menu.lst, or move it down the list so you default to the -15 one, until you somehow the -16 fixed.

---

### Post by jrharvey on 2007-10-09
Ok well i think i might just delete it but can I delete it with synaptic or should I use another method.

---

### Post by jrharvey on 2007-10-09
i really dont want to mess anything up in my current kernel

---

### Post by dabl on 2007-10-09
Did you, perchance, install a proprietary video driver?  Kernel upgrades will normally "break" a proprietary driver installation, and so you'll need to reinstall the driver.

BTW, at that "dead" or "frozen" black screen, did you try Alt-F1 and/or Ctrl-Alt-F1?  :)

---

### Post by jrharvey on 2007-10-09
Ok i will try it and tell you how it works out.

---

### Post by jrharvey on 2007-10-09
NO it did not do anything at all. I did install a driver for my nvidia card and im sure that has something to do with it but not sure what to do. Alt-F1 and Ctrl-Alt-F1 did not do anything.

---

### Post by fjgaude on 2007-10-09
From my experience with nVidia Ubuntu, Linux usually works with any of them.

One other thing, while in -15 have you tried updating using Synaptic, after when in Synaptic clicking on Reload?

---

### Post by jrharvey on 2007-10-09
im not sure what you mean. What about synaptic?

---

### Post by jrharvey on 2007-10-09
is the -16 the latest kernel or is there a newer one???

---

### Post by fjgaude on 2007-10-09
It's the front end to apt-get. You find it in System/Administartion.

Or to update things you use apt-get update then upgrade to update your system. This will tell if all has gone well during the last update.

Synaptic is terrific because of all the things it has installed.

---

### Post by jrharvey on 2007-10-09
I do know synaptic but i was unsure what you wanted me to do with it. I was asking about synaptic because I was wondering if i could remove the -16 kernel from there. Also if I did do this I wanted to make sure I selected the right thing to remove or if I should even use synaptic?

---

### Post by jrharvey on 2007-10-09
apt get update and upgrade said 0 installed and 0 upgraded.

---

### Post by fjgaude on 2007-10-09
> **jrharvey said:**
> I do know synaptic but i was unsure what you wanted me to do with it. I was asking about synaptic because I was wondering if i could remove the -16 kernel from there. Also if I did do this I wanted to make sure I selected the right thing to remove or if I should even use synaptic?

Okay, you can use Synaptic to remove all files. Put in the Search box "kernel" and then when lots of stuff comes up carefully fine the 2.6.20-16 items and click on the boxes to remove them.

After that you could try an upgrade again and see if it works. It's up to you.

---

### Post by jrharvey on 2007-10-09
Thanks but I got kinda nervous when deleting the kernels so I aborted and just changed the default to -15. Im not sure what is wrong but im not gonna spend too much time worrying about it especcially when Gutsy is released in 10 days.

---

### Post by fjgaude on 2007-10-09
Okay, but we both learned a little as we have gone through the process, eh?

---

### Post by jrharvey on 2007-10-09
Haha yes, and thanks again.

---

