---
title: "uninstall windoze, resore grub"
date: 2006-11-18
forum: General Help
---

### Post by spykecub on 2006-11-18
I installed Dapper a few months ago first as a dual boot with windows xp, have since upgraded to Edgy - LOVE IT

Since I've installed Ubuntu I haven't booted to Windows even ONCE. Nope, not once. So... don't need it anymore, and wouldn't mind getting the space back for storage/backup/anything other than windows.

Problem is, grub hasn't really worked since I've installed Ubuntu. My system has always booted directly into Windows without even asking me if that's what I wanted. I use the livecd to boot into Ubuntu (by using the "boot from main hard disk" when the cd boots)

So the question is obvious. How to I get rid of windows, and somehow get the mbr to use grub?

Here's the overview of what's happening on my hard drive: sda1 being the windows installation, sda3 where my Ubuntu is - sda2 is the swap partition and a partition for backup.

[[IMG]http://img296.imageshack.us/img296/599/screenshotvd2.th.gif[/IMG]](http://img296.imageshack.us/my.php?image=screenshotvd2.gif)

Thanks in advance - looking forward to living with only one OS ;)


p.s. I have searched for solutions on this forum, but all the similar problems / solutions seem just a *little* bit different from my situation...

---

### Post by funkyade on 2006-11-18
You need to -

1. reinstall grub to the master boot record (MBR)
2. change grub.conf or menu.lst to point to your /boot partition and the kernel you want to use.
3. reboot your machine.

You will need to reconfigure grub once you have booted into your main system.

first step might be to -
```
sudo aptitude reinstall grub
```

then you could follow this, if you want to get your hands dirty -
[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10) specifically the bit entitle "Alternative: Setting up GRUB using manual instructions"
I would follow this guide but change references to /boot/grub/grub.conf with /boot/grub/menu.lst


then check grub.conf to make sure everything is okay.
```
sudo nano -w /boot/grub/menu.lst
```

then check these pages -

[www.gnu.org/software/grub/](www.gnu.org/software/grub/)

hth

---

### Post by spykecub on 2006-11-19
*sigh*

Don't hate me, but I think I've discovered that I'm a grub n00b.

I've reinstalled grub like you said, checked out /boot/grub/menu.lst and found everything to be ok, and I'm still getting booted directly into windows. GRRR!!

But, I'm open enough to know that something must be wrong about my menu.lst:

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
# kopt=root=UUID=99cd78d1-e133-4250-913e-a8bbe2a43f47 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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

title		Ubuntu, kernel 2.6.17-10-386
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=99cd78d1-e133-4250-913e-a8bbe2a43f47 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=99cd78d1-e133-4250-913e-a8bbe2a43f47 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=99cd78d1-e133-4250-913e-a8bbe2a43f47 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=99cd78d1-e133-4250-913e-a8bbe2a43f47 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=99cd78d1-e133-4250-913e-a8bbe2a43f47 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=99cd78d1-e133-4250-913e-a8bbe2a43f47 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=UUID=99cd78d1-e133-4250-913e-a8bbe2a43f47 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=UUID=99cd78d1-e133-4250-913e-a8bbe2a43f47 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


```

Any ideas on how to fix the problem??

---

### Post by spykecub on 2006-11-19
Umm - scratch that - I now have grub loading on boot (YAY!), but it's telling me that the partition (hd1,2) doesn't exist.

When I boot from the cd, the partition (hd1,2) is easily found and booted no problem.

*sigh*

---

### Post by funkyade on 2006-11-20
okay try this -

1. comment out the map commands at the bottom of menu.lst. (Don't delete this is just a hunch)
2. comment out savedefault from the windows entry, you already have it on the ubuntu one add it to the ubuntu one.
3. try rebooting.

---

### Post by spykecub on 2006-11-20
Still didn't work - i get the same error message telling me that (hd1,2) doesn't exist.

Might help to know how I set up grub?

[COLOR="Red"]grub> root (hd1,2)[/COLOR]   (my ubuntu installation - see the screenshot)
[COLOR="Red"]grub> setup (hd1)[/COLOR]    (Installed GRUB in the MBR of the drive ubuntu is on, and where my computer boots)
[COLOR="Red"]grub> quit[/COLOR]

I've looked through the documentation and I can't find anything relevant. I'm not entirely sure why booting from the cd and accessing the same grub installation works, but booting into my hard drive doesn't.

Could it have something to do with the fact that grub is in the MBR (hd1) of the same drive that /boot is found, and somehow grub thinks /boot is on (hd0,1) instead??

Ok, grabbing at straws I guess, but this confuses the heck outta me!!!

---

### Post by spykecub on 2006-11-20
p.s. the hard drive i'm booting from is /dev/sda1 - I also have a /dev/hda1 connected to the ide port - maybe that has something to do with my problems??

---

### Post by funkyade on 2006-11-21
You need to confirm which hard drive your computer actually boots off, be it HDA1, SDA1 or whatever.

Have a look in your BIOS and look for something called the 'boot order'. The BIOS can be accessed by looking at the screen that pops up when you first turn on your computer, it will say something like 'Press DEL to enter setup' or something similar.

Once you know which one it is then it should get alot easier.

I would advise booting off the IDE drive set as your primary master. It makes things slightly easier again. That will then become hd0 as far as GRUB is concerned.

you will then need to do
```

grub> root (hd0,0)
grub> setup (hd0)
grub quit

```

Your existing menu.lst should be valid in any case.

---

