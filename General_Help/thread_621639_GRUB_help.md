---
title: "GRUB help"
date: 2007-11-23
forum: General Help
---

### Post by Dvorakis on 2007-11-23
I don't know much about configure grub...but I just installed windows and a newly created partition,but when I startup GRUB simply takes me into my Ubuntu partition,without asking,

Any help?

---

### Post by RJ Fighter on 2007-11-23
Hit escape as soon as GRUB appears to select which OS you want to boot from.

---

### Post by helloimalemur on 2007-11-23
i had that problem. :[ 
i reinstalled grub and the works.. didnt work..
i ended up installin windows then linux.. with a partition as "/boot".. works fine

---

### Post by erfahren on 2007-11-23
[just about anything you need to know about GRUB](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by meierfra on 2007-11-23
open a terminal (Applications->Accessories->Terminal) and post the output of


```
sudo fdisk -l
```

and

```
cat /boot/grub/menu.lst
```
(both "l" are lowercase L, not the number one)

---

### Post by Dvorakis on 2007-11-24
```
Disk /dev/hda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6635f736

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2677    21502971   83  Linux
/dev/hda2   *        2678        4669    16000740    7  HPFS/NTFS
/dev/hda3            4670        4870     1614532+   5  Extended
/dev/hda5            4670        4870     1614501   82  Linux swap / Solaris

```
Any my menu.lst
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
# kopt=root=UUID=88286246-2c20-484e-a574-31685840bfe6 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=88286246-2c20-484e-a574-31685840bfe6 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=88286246-2c20-484e-a574-31685840bfe6 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=88286246-2c20-484e-a574-31685840bfe6 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet

title           Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=88286246-2c20-484e-a574-31685840bfe6 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu 7.10, kernel 2.6.17-12-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-12-generic root=UUID=88286246-2c20-484e-a574-31685840bfe6 ro quiet splash
initrd          /boot/initrd.img-2.6.17-12-generic
quiet

title           Ubuntu 7.10, kernel 2.6.17-12-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-12-generic root=UUID=88286246-2c20-484e-a574-31685840bfe6 ro single
initrd          /boot/initrd.img-2.6.17-12-generic

title           Ubuntu 7.10, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=UUID=88286246-2c20-484e-a574-31685840bfe6 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet

title           Ubuntu 7.10, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=UUID=88286246-2c20-484e-a574-31685840bfe6 ro single
initrd          /boot/initrd.img-2.6.17-10-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Ubuntu
root (hd0,1)
configfile /wubi/boot/grub/menu.lst



title Ubuntu
root (hd0,1)
configfile /wubi/boot/grub/menu.lst

```

---

### Post by meierfra on 2007-11-24
Try this:

Open the file "menu.lst" via
```
 gksudo gedit /boot/grub/menu.lst
```
("l" is a lowercase L)

Change "timeout 3" to "timeout 10"

Change "hiddenmenu" to "#hiddenmenu"

Add this to the end of the file:


title Windows XP
root (hd0,1)
makeactive
chainloader +1


Save the file and reboot. The grub-menu should appear and selecting "Windows XP" should boot you into windows.

Did you used to have "wubi"?
Did you add "title Ubuntu, root (hd0,1),  configfile /wubi/boot/grub/menu.lst" to menu.lst?

---

### Post by Dvorakis on 2007-11-24
Never had Wubi,and never added that myself.

I'll try your suggestions.

---

