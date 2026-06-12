---
title: "Help please"
date: 2007-01-31
forum: General Help
---

### Post by spiked79 on 2007-01-31
I am brand new to Linux and have recently (Saturday) just installed ubuntu 6.06 on my computer and I am having the following problem:

When I first boot everything goes well until it hits the loading screen.  Then it just sits on the "Mounting root file system".  I have to reboot and go into the "recovery mode".  Once that is finished loading I then can reboot once more and get into the GUI look of ubuntu.

Any help on this would be gretly appreciated.

Cheers,
spiked79

---

### Post by taurus on 2007-01-31
Can you post the outputs of these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by spiked79 on 2007-01-31
The result for sudo fdisk -l:

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/tracks, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

    Device Boot     Start       End           Blocks    ID   System
/dev/hda1   *            1    14405    115708131    83   Linux
/dev/hda2           14406   14593       1510110      5   Extended
/dev/hda5           14406   14593       1510078+  82   Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/tracks, 4866 cylinders
Units = culinders of 16065 * 512 = 8225280 Bytes

    Device Boot     Start       End           Blocks    ID   System
/dev/hda1   *            1      4111      33021576     c    W95 FAT32 (LBA)

The result of cat/etc/fstab:

# /etc/fstab: static file system information
#
# <file system>   <mount point>   <type>  <options>   <dump>  <pass>
proc                    /proc                 proc       defaults       0              0
//dev/hda1          /                       ext3        defaults, errors=remount-ro 0       1
/dev/hda5           none                 swap        sw              0              0
/dev/hda            /media/cdrom0   udf, iso9660 user, noauto      0              0

Hope this helps.

Cheers,
Spiked79

---

### Post by taurus on 2007-01-31
You have an extra / and extra space in /etc/fstab for / partition.  Therefore, edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and remove an extra / from this line

```
//dev/hda1 / ext3 defaults, errors=remount-ro 0 1
```
so now it would look like this.

```
/dev/hda1  /   ext3   defaults,errors=remount-ro   0   1
```
Save it and reboot.  See what happens now.

---

### Post by spiked79 on 2007-01-31
Sorry about the confusion the line that started with // should have only had one of those /.  It was my fault, typing error.

Cheers,
Spiked79

---

### Post by taurus on 2007-01-31
Then, what does your /boot/grub/menu.lst look like?

```
cat /boot/grub/menu.lst
```

---

### Post by spiked79 on 2007-01-31
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
# kopt=root=/dev/hda1 ro

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

title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-27-386
boot

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title           Windows 95/98/Me
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

Found an easier way to copy these over.  Hope something in here helps.

Cheers,
Spiked79

---

