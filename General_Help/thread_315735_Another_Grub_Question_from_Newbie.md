---
title: "Another Grub Question from Newbie"
date: 2006-12-09
forum: General Help
---

### Post by wireddad on 2006-12-09
](*,) I am trying to make windows the default boot.  I have been reading the grub threads but still lost.

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda5 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Most say to change 0 to 4.  What?  Am I to change, under windows section, root (hd0,0) to (hd0,4)?  And change the ubuntu sections to (hd0,0)?  Is this all? :confused:

---

### Post by Herman on 2006-12-10
Hello wireddad,
Here's a link that will show you what you need to do if you want to make Windows the default booted operating system, Changing the default (operating system booted by the timer)........................................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc")
Regards, Herman :D

---

### Post by wireddad on 2006-12-10
> **Herman said:**
> Hello wireddad,
Here's a link that will show you what you need to do if you want to make Windows the default booted operating system, Changing the default (operating system booted by the timer)........................................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc")
Regards, Herman :D

Thank you Herman.  So if is read the Grub Page and understand correctly,

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

I will just have to change:
[B]# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
**_default		0_**[/B]

value to 4, right?  I want to be sure before doing something silly because I still need to get to windows.

---

### Post by nikhilk on 2006-12-10
> **wireddad said:**
> **_default 0_**
value to 4, right?
That is correct.

---

### Post by hadiriazi on 2006-12-10
Hi;

You could also use [grubED]("http://ubuntuforums.org/showthread.php?t=228104") a simple GUI app that does it for you :)

---

### Post by wireddad on 2006-12-10
Thank you.  I will need to re-learn how to install programs first among other things.  I will keep these recommended programs in mind.  For now I will just edit the file directly.

---

### Post by wireddad on 2006-12-10
Ok.  I believe I have installed GrubEd correctly following the instructions...took a little bit.  Now how do I run it?  I've tried gksudo, sudo, and just GrubEd itself.  Please point me.  Thanks.

---

### Post by Tomosaur on 2006-12-10
There's a launcher included in the download, so you should be able to just copy and paste that onto your desktop and double click it.

---

### Post by wireddad on 2006-12-10
I found the file, I think, Launch GrubEd.  When I click on it I get:
[B]KDEInit could not launch 'gksudo'.:
Could not find 'gksudo' executable.
[/B]

---

### Post by wireddad on 2006-12-10
I was using Kubuntu.  That is probably why the command gksudo did not work.  I have just loaded Edgy.  I will try to load GrubEd again.

---

### Post by wireddad on 2006-12-10
GrubEd installed and working good under gnome.  Thanks for y'all help.

---

