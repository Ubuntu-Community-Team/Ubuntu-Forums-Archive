---
title: "arduous error 17"
date: 2008-01-28
forum: General Help
---

### Post by thedooropened on 2008-01-28
hey guys, new to the forum, new to linux, and i like it so far, BUT.

when i boot up my computer and get to the OS selecter thing screen, it has several options.

couple of ubuntu kernel generic things
memtest
Other Operating Systems
Windows XP Home Edition
Ubuntu 7.04 (on /dev/sda5)


i select ubuntu, as the obvious choice, and it gives me the good ole error 17 cannot mount drive.

is there a way in which my computer is reading things in the wrong order?

i'd appreciate the help a ton.

---

### Post by codesplice on 2008-01-28
Could you post up the contents of your /etc/fstab and /boot/grub/menu.lst files?

---

### Post by thedooropened on 2008-01-28
but of course, if you tell me how. i am super new.

---

### Post by codesplice on 2008-01-28
Since you can't boot your system, you'll have to do it from the LiveCD.

Once it's booted up, click the Computer icon on the desktop.  Navigate to whichever harddisk partition has your Linux install - you'll have to guess and check on that most likely.  Maneuver around until you're in the /boot/grub directory, and open menu.lst.  Fire up Firefox, and post the contents of that file.  Do the same for the /etc/fstab.

---

### Post by thedooropened on 2008-01-28
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5230fa56-7581-41ff-9553-13586e424e13 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5230fa56-7581-41ff-9553-13586e424e13 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

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
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 7.04 (7.04) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/sda5 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


and now for the other one.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=5230fa56-7581-41ff-9553-13586e424e13 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=9d349967-6339-4750-9d54-18287b47137b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by codesplice on 2008-01-28
Before you start tinkering with the menu.lst file, back it up.

Just for fun, try changing the root=UID=.... parts of the menu.lst to "root=/dev/sda3".  Also, add the word "boot" to a line directly below the first two Ubuntu entries.

Reboot and see what happens. :)

---

### Post by thedooropened on 2008-01-28
it isnt letting me adjust it.

i need permussions.

how abouts do i go about that?

---

### Post by codesplice on 2008-01-28
I like to do it in the terminal.

Navigate to the folder containing the file, right click empty space, open terminal.

Then,

```
$ sudo nano /boot/grub/menu/lst
```

CTRL+X to save and exit.

---

