---
title: "Installed XP on other HDD, now cant boot Ubuntu. (grub messed up)"
date: 2007-10-04
forum: General Help
---

### Post by fusion.fake on 2007-10-04
The situation:

I have 2 harddrives, one 320gb one 250gb. I always had Windows Vista on the 320gb one, later i decided to install Ubuntu, wich all went well. so now, a few months later, i decided to remove vista, (format the 320gb harddrive) and install xp there. Now the computer boots immediatley to XP and not ubuntu. I switched the cables of the hard drives so i can get the GRUB boot screen, but i couldnt boot ubuntu from there. I read a few suggestions, i also tried Super Grub Disk, what automaticly fixes GRUB, but this hasnt been helpfull. i managed to boot Ubuntu through direct partition loading through the super disk, but how can i setup GRUB again, so everything works like it used to ?


this is some info about the drives in fdisk :
sda1 is my XP partition probably, and sdb6 is the Ubuntu partition. sdb5 is a old ntfs partition i keep data on.

```
Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *           1       38912   312560608+   7  HPFS/NTFS

Schijf /dev/sdb: 250.0 GB, 250059350016 bytes
16 koppen, 63 sectoren/spoor, 484521 cilinders
Eenheid = cilinders van 1008 * 512 = 516096 bytes

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdb1   *           2      484519   244197072    5  Uitgebreid
/dev/sdb5               2      387526   195312568+   7  HPFS/NTFS
/dev/sdb6          387527      477197    45194152+  83  Linux
/dev/sdb7          477198      484519     3690256+  82  Linux wisselgeheugen
```

---

### Post by fusion.fake on 2007-10-04
I dont know exactly what i did, but grub is active again now, and boots correctly in ubuntu. But the old entry of Vista is still in grub and xp is no where to be found in the boot menu. How can i edit it to show XP so i can boot that aswell?

---

### Post by fusion.fake on 2007-10-04
any1?

---

### Post by fusion.fake on 2007-10-05
:icon_frown:

---

### Post by meierfra on 2007-10-05
The vista entree in grub might already  boot to  XP. If not post the output of

```
sudo fdisk -l
```

and

```
cat /boot/grub/menu.lst
```

(both l's are lower case L)

---

### Post by fusion.fake on 2007-10-06
i tried vista but the problem is now i cant mount the NTFS hard disk its unreadable everywhere, but i haven't done anything with it... i seriously am totally lost now. i dont want to reinstall xp and maybe even get the same error cause i don't think i did anything wrong..

anyways, thanks for your reply, my sudo fdisk -l is part dutch cause my ubuntu is dutch, if theres something you don't understand please post, ill translate.

**sudo fdisk -l**
```

fusion@fusion-desktop:~$ sudo fdisk -l
Password:

Schijf /dev/sda: 320.0 GB, 320072933376 bytes
255 koppen, 63 sectoren/spoor, 38913 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *           1       38912   312560608+   7  HPFS/NTFS

Schijf /dev/sdb: 250.0 GB, 250059350016 bytes
16 koppen, 63 sectoren/spoor, 484521 cilinders
Eenheid = cilinders van 1008 * 512 = 516096 bytes

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdb1   *           2      484519   244197072    5  Uitgebreid
/dev/sdb5               2      387526   195312568+   7  HPFS/NTFS
/dev/sdb6          387527      477197    45194152+  83  Linux
/dev/sdb7          477198      484519     3690256+  82  Linux wisselgeheugen

```

**cat /boot/grub/menu.lst**

```
fusion@fusion-desktop:~$ cat /boot/grub/menu.lst
gfxmenu /boot/grub/message.ubugrey
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=f39da9ac-9c27-41ea-8e03-955dce0aa734 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,5)

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

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd1,5)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=f39da9ac-9c27-41ea-8e03-955dce0aa734 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd1,5)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=f39da9ac-9c27-41ea-8e03-955dce0aa734 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,5)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=f39da9ac-9c27-41ea-8e03-955dce0aa734 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,5)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=f39da9ac-9c27-41ea-8e03-955dce0aa734 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd1,5)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

---

### Post by meierfra on 2007-10-06
Your "menu.lst" looks o.k.  So I need more information:

What error message do you get when you try to boot windows through the grub menu?

Can you still boot into windows by switching the hard drive cables back ?

Do you know on which of the hard drive grub is installed ?  (from the menu.lst,  I would say  it is the 320GB windows drive) 

What  did you do to get ubuntu to boot? Did you switch the hard drives cables back?

---

### Post by fusion.fake on 2007-10-07
Now i cant boot ubuntu anymore, only through GRUB super disk after selection the partition...

i've lost it :P i think i;ll wait for ubuntu 7.10 and then reinstall everything again... thanks for the help though

---

