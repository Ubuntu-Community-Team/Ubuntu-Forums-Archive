---
title: "[SOLVED] Just Installed Xubuntu, but I need help setting up GRUB to boot to XP"
date: 2007-09-05
forum: General Help
---

### Post by RAV TUX on 2007-09-05
If any one could help me with this it would be greatly appreciated.

---

### Post by merlinus on 2007-09-05
Post the usual:

```

sudo fdisk -l
cat /boot/grub/menu.lst

```

-merlin

---

### Post by rsambuca on 2007-09-05
Are you sure you have XP on your drive, amongst the other 10 OS's you have going!!??

---

### Post by RAV TUX on 2007-09-05
> **merlinus said:**
> Post the usual:

```

sudo fdisk -l
cat /boot/grub/menu.lst

```-merlin

Could I have fried my XP on sda1?
```

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19451   156240126    7  HPFS/NTFS
/dev/sda2           19452       19464      104422+  83  Linux
/dev/sda3           19465       38903   156143767+  8e  Linux LVM

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19075   153219906   83  Linux
/dev/sdb2           19076       19452     3028252+   5  Extended
/dev/sdb5           19076       19452     3028221   82  Linux swap / Solaris
```I'm not sure what is installed on sda2 and sda3?

Should XP still be working?

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# kopt=root=UUID=f0b59303-9bb6-4f52-9408-6ad7ba91e9f7 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=f0b59303-9bb6-4f52-9408-6ad7ba91e9f7 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=f0b59303-9bb6-4f52-9408-6ad7ba91e9f7 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title windows xp
root (hd0,0)
rootnoverify
makeactive
chainloader +1
boot
```

---

### Post by merlinus on 2007-09-05
This looks good to me.  Does the grub menu appear at boot up, and if so, is there an option to run xp?

Also, what is the boot order of your hdds?

And what does this show:

```

cat /boot/grub/device.map

```

-merlin

---

### Post by confused57 on 2007-09-05
You can try:
```
title windows xp
rootnoverify (hd0,0)
makeactive
chainloader +1
```

Hello merlin,
   Good questions, if the above entry doesn't work.

---

### Post by rsambuca on 2007-09-05
Hmmm...  That looks like it should work.  In a round-a-bout way, you could perhaps do the "fixmbr" from the xp installation cd, and then use a linux live cd to reinstall grub.

---

### Post by RAV TUX on 2007-09-06
> **merlinus said:**
> This looks good to me.  Does the grub menu appear at boot up, and if so, is there an option to run xp?

Also, what is the boot order of your hdds?

And what does this show:

```

cat /boot/grub/device.map

```-merlin

Windows XP is listed on the boot menu but when I select it I get:

```
grub error 11 unrecognized device string
```

I ran the root ( in the grub command line and the possible disk are: fd0 hd0 hd1

Also the answer to your other question is:
```
 cat /boot/grub/device.map
(hd0)   /dev/sda
(hd1)   /dev/sdb
```

---

### Post by merlinus on 2007-09-06
Change xp entry in menu.lst to what confused57 recommended a couple of posts ago:

title windows xp
rootnoverify (hd0,0)
makeactive
chainloader +1

---

### Post by rsambuca on 2007-09-06
Have you checked the boot order of the drives in your bios to make sure they match the grub?

---

### Post by RAV TUX on 2007-09-06
> **confused57 said:**
> You can try:
```
title windows xp
rootnoverify (hd0,0)
makeactive
chainloader +1
```Hello merlin,
   Good questions, if the above entry doesn't work.

This actually worked but I got the following message

> Windows could not start because the following file is missing or corrupt

\WINDOWS\SYSTEM32\CONFIG\SYSTEM

You can attempt to repair this file by starting windows setup

using the original setup cd-rom

Select 'r' at the first screen to start repair

So I tried to repair windows but failed so I did I clean install of XP and then I  did a clean install of Xubuntu.

Everything is working fine and this time I was able to select the set up of my ID under Windows XP in the Xubuntu install and now everything works great!

grub loads just as it should and Windows XP is listed and I can boot with no problems. Thanks for the help everyone!

I am the proud users of a dual boot to Xubuntu and Windows XP ;)

---

### Post by merlinus on 2007-09-06
Gotta love those success stories!  Well done!

-merlin

---

### Post by rsambuca on 2007-09-06
Mark it [Solved], my boy.  Albeit the hard way.

---

### Post by RAV TUX on 2007-09-06
> **rsambuca said:**
> Mark it [Solved], my boy.  Albeit the hard way.
[Solved] it is! ;)

Thanks again to everybody who helped!

---

