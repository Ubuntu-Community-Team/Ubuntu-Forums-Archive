---
title: "Grub restore?"
date: 2007-10-19
forum: General Help
---

### Post by kdarkentity on 2007-10-19
Recently i installed feisty server edition onto my laptop on a small partition and when i did this i believe my newer grub from gutsy was replaced by the grub from the server edition. How can i either reinstall the new grub or how can i make it the default grub again?

---

### Post by rsambuca on 2007-10-19
> **kdarkentity said:**
> Recently i installed feisty server edition onto my laptop on a small partition and when i did this i believe my newer grub from gutsy was replaced by the grub from the server edition. How can i either reinstall the new grub or how can i make it the default grub again?

It shouldn't matter which grub you are using, but if you wish to switch, you need to know the partition on which the Gutsy partition is.  Then```
sudo grub
```at the grub> prompt that comes up, enter ```
find /boot/grub/stage2
```It should spit out a couple of locations for your grub loader in the form (hd***x,y***).  As long as you know which is your Gutsy partition, then enter```
root (hdx,y)
```, where hdx,y is the Gutsy partition.  Then ```
setup (hd0)
```to write it to the MBR.  Finally type 'quit' and you are done.  The next time you boot up, you will be using the Gutsy grub, but keep in mind that since you installed Feisty afterwords, you will have to manually add it to the Gutsy grub menu.lst.

---

### Post by kdarkentity on 2007-10-19
Sweet! thanks you've been a bid help!!, now could you tell me how to add fesity server into my grub boot list, or could i simply find it under "other operating systems"?

---

### Post by rsambuca on 2007-10-19
Post the output of the following:

cat /boot/grub/menu.lst
sudo fdisk -l

---

### Post by kdarkentity on 2007-10-20
kevin@kevin-laptop:~$ 
kevin@kevin-laptop:~$ cat /boot/grub/menu.lst
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
# WARNING: If you are using dmraid do not use 'savedefault' or your
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
color red/black red/black

#A splash image for the menu
splashimage=(hd0,0)/boot/grub/splashimages/shot00028.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=2b25a8b8-6d60-4ed9-ac98-b0eac5a69542 ro

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
# defoptions=quiet splash vga=789

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
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=2b25a8b8-6d60-4ed9-ac98-b0eac5a69542 ro quiet splash vga=789
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=2b25a8b8-6d60-4ed9-ac98-b0eac5a69542 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, kernel 2.6.22-13-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-13-generic root=UUID=2b25a8b8-6d60-4ed9-ac98-b0eac5a69542 ro quiet splash vga=789
initrd          /boot/initrd.img-2.6.22-13-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-13-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-13-generic root=UUID=2b25a8b8-6d60-4ed9-ac98-b0eac5a69542 ro single
initrd          /boot/initrd.img-2.6.22-13-generic

title           Ubuntu 7.10, kernel 2.6.22-12-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-12-generic root=UUID=2b25a8b8-6d60-4ed9-ac98-b0eac5a69542 ro quiet splash vga=789
initrd          /boot/initrd.img-2.6.22-12-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-12-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-12-generic root=UUID=2b25a8b8-6d60-4ed9-ac98-b0eac5a69542 ro single
initrd          /boot/initrd.img-2.6.22-12-generic

title           Ubuntu 7.10, kernel 2.6.22-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-10-generic root=UUID=2b25a8b8-6d60-4ed9-ac98-b0eac5a69542 ro quiet splash vga=789
initrd          /boot/initrd.img-2.6.22-10-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-10-generic root=UUID=2b25a8b8-6d60-4ed9-ac98-b0eac5a69542 ro single
initrd          /boot/initrd.img-2.6.22-10-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista/Longhorn (loader)
root            (hd0,1)
savedefault
makeactive
chainloader     +1

kevin@kevin-laptop:~$ sudo fdisk -l
[sudo] password for kevin:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4fac9119

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7722    62026933+  83  Linux
/dev/sda2   *        9146       19458    82831360    7  HPFS/NTFS
/dev/sda3            7723        7950     1831410   83  Linux

Partition table entries are not in disk order
kevin@kevin-laptop:~$

---

### Post by rsambuca on 2007-10-20
You will need to add something like the following to the bottom of your /boot/grub/menu.lst:

```
title  Ubuntu Feisty 7.04 Server
root (hd0,2)
kernel /boot/vmlinuz-[COLOR="Red"]2.6.20-16-generic[/COLOR] root=/dev/sda3 ro quiet splash
initrd /boot/initrd.img-[COLOR="Red"]2.6.20-16-generic[/COLOR]
```The parts I highlighted in red will have to be changed to correspond to the correct kernel for the version of feisty you want to run.

---

### Post by kdarkentity on 2007-10-20
ok thanks ill try this, ill let you know if i run into problems

---

