---
title: "Changing Grub bootloader to boot windows by default"
date: 2006-08-13
forum: General Help
---

### Post by cptjaben on 2006-08-13
I recently convinced my friend to try dual-booting windows XP/ubuntu in order to convince him that ubuntu is superiour to windows. However, he spends a good deal of time playing World of Warcraft on windows because he can't figure out how to install his video card's drivers in Ubuntu. Is there a way  that one can edit Grub bootloader so that it can boot by defualt to windows until he can get WoW playing on Ubuntu?

Thanks Much,
cptjaben

---

### Post by vijirajan on 2006-08-13
You can do that by changing the "default" parameter in /boot/grub/menu.lst. Set that to the entry number for Windows. Remember entry numbers start with 0.

---

### Post by Athanasius on 2006-08-13
First you open your grub boot menu
> sudo gedit /boot/grub/menu.lst

Look towards the top and you will see
> ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

Notice it says "default 0" 0 is the current kernel that you are using.  

Now you have to look towards the bottom of the file and you will see
> ## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

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


The best way I know how to explain it is that you count how many times it says "title".  Since the numbering starts with "0", I would put the number "6" in the upper part of the file so you would change "default 0" to "default 6" or whatever number your Windows is at.

I am sorry if that is not clear enough.

---

### Post by cptjaben on 2006-08-14
Thanks for the help guys

cptjben

---

