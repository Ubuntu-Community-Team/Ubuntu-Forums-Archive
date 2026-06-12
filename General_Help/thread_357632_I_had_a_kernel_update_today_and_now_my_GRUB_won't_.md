---
title: "I had a kernel update today and now my GRUB won't load Ubuntu..."
date: 2007-02-09
forum: General Help
---

### Post by LPomfrey on 2007-02-09
My kernel got updated today, since then I can't log in to Ubuntu. GRUB keeps giving me an @Error 20@ How can I reinstall Grub so I can log in? :(

---

### Post by LPomfrey on 2007-02-09
Sorted this. Why is it that every time I get a kernel update I have to screw around with GRUB? :(

---

### Post by dannyboy79 on 2007-02-09
there is a tutorial for this, so that when you kernel gets updated you don't have to fix grub.

---

### Post by SuperMike on 2007-02-09
On this one, I wouldn't mess around in a forum unless you've been doing this awhile. I'd recommend calling Ubuntu support. Besides, I checked their prices and for end users at home, it's not that expensive at all. I hope I'm aloud to say this on the Ubuntu Forums, but I think that's the best option for helping you through this besides me telling you something and it get screwed up even worse.

---

### Post by LPomfrey on 2007-02-09
> **SuperMike said:**
> On this one, I wouldn't mess around in a forum unless you've been doing this awhile. I'd recommend calling Ubuntu support. Besides, I checked their prices and for end users at home, it's not that expensive at all. I hope I'm aloud to say this on the Ubuntu Forums, but I think that's the best option for helping you through this besides me telling you something and it get screwed up even worse.

I'm open to any suggestions this is the second time it's happened and the second time I've had to mess around with it to get it working. Not that I mind, it's just a little annoying having to get it working myself again, was kinda hoping someone had the same problem and had a quick fix.

---

### Post by LPomfrey on 2007-02-09
> **dannyboy79 said:**
> there is a tutorial for this, so that when you kernel gets updated you don't have to fix grub.

Do you have a link?

---

### Post by dannyboy79 on 2007-02-10
according to other threads in this forum, this is what 1 person stated.

I changed kopt=/dev/sda3 to kopt=/dev/hda3 (not groot). After running update-grub it kept hda3 as the root device . Thank you!

so find your #kopt line and change that to whatever your main hard drive and partition where your root partition is. on the other hand I found this, [http://www.ubuntuforums.org/archive/index.php/t-64002.html](http://www.ubuntuforums.org/archive/index.php/t-64002.html)

it talkas about adding your menu.lst boot entries AFTER the section that talks about automagically updating grub boot lines. try that. good luck. thsi is what my grub looks like and mine never does what you're saying.

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
timeout		3

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
# kopt=root=/dev/hdc2 ro noapic

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,1)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-27-686
root		(hd0,0)
kernel		/vmlinuz-2.6.15-27-686 root=/dev/hdc2 ro quiet noapic
initrd		/initrd.img-2.6.15-27-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-686 (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.15-27-686 root=/dev/hdc2 ro single noapic
initrd		/initrd.img-2.6.15-27-686
boot

title		Ubuntu, kernel 2.6.15-26-686
root		(hd0,0)
kernel		/vmlinuz-2.6.15-26-686 root=/dev/hdc2 ro quiet noapic
initrd		/initrd.img-2.6.15-26-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-686 (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.15-26-686 root=/dev/hdc2 ro single noapic
initrd		/initrd.img-2.6.15-26-686
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

what is weird though is that  I don't have any entries OUTSIDE of the automagic section so I guess I am not sure what to tell you.

---

### Post by cmost on 2007-02-10
It's also highly irritating to have to recompile and reinstall the nvidia kernel module each time the Ubuntu devs decide to update the kernel.  Kernel updates should happen only when ABSOLUTELY NECESSARY!!!!  Considering Ubuntu is a newbie friendly OS and that updates are fetched automatically and presented to users via a nifty update manager...users aren't expecting a black screen or an X failure when they're through with updates.

---

