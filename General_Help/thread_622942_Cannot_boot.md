---
title: "Cannot boot"
date: 2007-11-25
forum: General Help
---

### Post by zephyrus17 on 2007-11-25
After trying to play around with a splash screen, I killed the boot.

It says this at the RECOVERY grub:
> VFS: Cannot open root device "UUID=afae1f7e0-e0dd-4f14-a2d5-bd2fefeaff24" or unknown-block(0,0)
Please append a correct "root=" boot option
Kernel panic - not syncing: VFS Unable to mount root fs on unknown-block(0,0)

Here's the boot.lst:

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=d2cc087a-0681-4c63-959f-0241277dc47f ro

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
## e.g. defoptions resume=/dev/hda5
# defoptions=quiet splash locale=en_SG

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
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d2cc087a-0681-4c63-959f-0241277dc47f ro quiet splash locale=en_SG
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d2cc087a-0681-4c63-959f-0241277dc47f ro single
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
title		Dell Utility Partition
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



Is there a way to fix it?

---

### Post by teryowen on 2007-11-25
what was it that you did in the first place? what did you edit or change go back and see if you can change it back.

---

### Post by zephyrus17 on 2007-11-25
Sorry about that. I tried to install Usplash Theme - Fingerprint  0.2 ALPHA 1.
I followed the instructions on [https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765]("https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765")

Well, before I edited it, I did a back up. I tried to change the .lst_bck to .lst, and pasted it in grub. That didn't help much.

I'm guessing that > sudo update-initramfs -u did something bad.

---

### Post by zephyrus17 on 2007-11-25
Bump.

---

### Post by teryowen on 2007-11-25
hey try this in terminal:

```
sudo apt-get install usplash
```

EDIT:

Sorry, you should do the following actually

```

sudo apt-get update
sudo apt-get install usplash
sudo dpkg-reconfigure usplash

```

---

### Post by meierfra on 2007-11-25
You might try to replace "initrd.img..." in /boot by  its backup file" (But  first  make a different backup of  the current "initrd.img..."

---

### Post by zephyrus17 on 2007-11-25
Teryowen: Problem is that I can't access ubuntu in the first place, so I can't get into the terminal.

meierfra: Thanks! It worked like a charm.

Thanks for all the help, guys.

---

### Post by teryowen on 2007-11-25
i meant through recovery mode, but good to hear that everything is good now

---

