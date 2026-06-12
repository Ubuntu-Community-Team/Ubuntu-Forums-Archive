---
title: "After merging partitions with gparted GRUB returns error 17"
date: 2006-12-14
forum: General Help
---

### Post by patientjob on 2006-12-14
Hello everybody. After deciding that i need to merge two partitions using gparted from live CD my GRUB decided that error 17 is what i deserve. I searched and tried a lot before posting therefore i am afraid that my GRUB looks like the gordian knot with few nasty errors :mrgreen: . Any help will be appreciated 
Thanks in advance!!
(PS: wife doesn't like that computer caput 8) , rough seas ahead)

---

### Post by bulldog on 2006-12-14
Well if you can give the fdisk -l outcome and your menu.lst as well we have a look.
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 82.3 GB, 82347195904 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 3924 31519498+ 7 HPFS/NTFS
/dev/sda2 3925 9760 46877670 83 Linux
/dev/sda3 9761 10011 2016157+ 5 Extended
/dev/sda5 9761 10011 2016126 82 Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdb1 2 38913 312560640 f W95 Ext'd (LBA)
/dev/sdb5 2 22204 178345566 7 HPFS/NTFS
/dev/sdb6 35023 38913 31254426 b W95 FAT32
/dev/sdb7 22205 35022 102960553+ b W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdd: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdd1 * 1 36481 293033601 b W95 FAT32
```

You have one partition less,as I saw,so your menu.lst  probably points to the wrong partition.
Fixed in a few minutes.```

# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title Ubuntu, kernel 2.6.15-27-386
root (hd0,1)
kernel /boot/vmlinuz-2.6.15-27-386 root=/dev/sda2ro quiet splash
initrd /boot/initrd.img-2.6.15-27-386
savedefault
boot

title Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.15-27-386 root=/dev/sda2 ro single
initrd /boot/initrd.img-2.6.15-27-386
boot

title Ubuntu, kernel 2.6.15-26-686
root (hd0,1)
kernel /boot/vmlinuz-2.6.15-26-686 root=/dev/sda2 ro quiet splash
initrd /boot/initrd.img-2.6.15-26-686
savedefault
boot

title Ubuntu, kernel 2.6.15-26-686 (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.15-26-686 root=/dev/sda2 ro single
initrd /boot/initrd.img-2.6.15-26-686
boot

title Ubuntu, kernel 2.6.15-23-386
root (hd0,1)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro quiet splash
initrd /boot/initrd.img-2.6.15-23-386
savedefault
boot

title Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro single
initrd /boot/initrd.img-2.6.15-23-386
boot

title Ubuntu, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows NT/2000/XP (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1

```

I changed the menu.lst for you.
If windows is on the same disk as Ubuntu on the first partition,this should work this way.
You have to take a look at your fstab too,if the boot partition is listed as sda3 and change it into sda2```
sudo cp /etc/fstab /etc/fstab_backup
```
```
gksudo gedit /etc/fstab
```to alter it.
You can copy and paste this menu.lst to your menu.lst and overwrite it,save as menu.lst and try to reboot.

---

### Post by patientjob on 2006-12-14
After continuing messing with the GRUB i managed to make windows boot but ubuntu still doesn't want to abide. Help is still needed (even if wife calmed down and the seas are calm and smooth :cool: )

---

### Post by patientjob on 2006-12-14
fdisk -l shows:


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 82.3 GB, 82347195904 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 3924 31519498+ 7 HPFS/NTFS
/dev/sda2 3925 9760 46877670 83 Linux
/dev/sda3 9761 10011 2016157+ 5 Extended
/dev/sda5 9761 10011 2016126 82 Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdb1 2 38913 312560640 f W95 Ext'd (LBA)
/dev/sdb5 2 22204 178345566 7 HPFS/NTFS
/dev/sdb6 35023 38913 31254426 b W95 FAT32
/dev/sdb7 22205 35022 102960553+ b W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdd: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdd1 * 1 36481 293033601 b W95 FAT32

---

### Post by patientjob on 2006-12-14
menu.lst follows:

# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##
title Ubuntu, kernel 2.6.15-27-386
root (hd0,2)
kernel /boot/vmlinuz-2.6.15-27-386 root=/dev/sda3 ro quiet splash
initrd /boot/initrd.img-2.6.15-27-386
savedefault
boot

title Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.15-27-386 root=/dev/sda3 ro single
initrd /boot/initrd.img-2.6.15-27-386
boot

title Ubuntu, kernel 2.6.15-26-686
root (hd0,2)
kernel /boot/vmlinuz-2.6.15-26-686 root=/dev/sda3 ro quiet splash
initrd /boot/initrd.img-2.6.15-26-686
savedefault
boot

title Ubuntu, kernel 2.6.15-26-686 (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.15-26-686 root=/dev/sda3 ro single
initrd /boot/initrd.img-2.6.15-26-686
boot

title Ubuntu, kernel 2.6.15-23-386
root (hd0,2)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/sda3 ro quiet splash
initrd /boot/initrd.img-2.6.15-23-386
savedefault
boot

title Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/sda3 ro single
initrd /boot/initrd.img-2.6.15-23-386
boot

title Ubuntu, memtest86+
root (hd0,2)
kernel /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows NT/2000/XP (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by bulldog on 2006-12-14
Well the work is done :D 
Look at my previous post and do what I have suggested.
Only take a look at your fstab cause it's possible your sda3 is listed but you should change it in sda2.
Than it should work.

---

### Post by patientjob on 2006-12-14
Worked just fine. Thank you very much:KS

---

