---
title: "Grubb xp not in the list."
date: 2008-01-05
forum: General Help
---

### Post by FzZZy on 2008-01-05
I had xp on my computer before i installed Ubuntu to day on own partition. But when i restarted en pressed esc to get in to grub xp wasn't in the list. How do i get windows in that list so i can boot it up agin?!

---

### Post by SOULRiDER on 2008-01-05
Ill help you out, but i need to know what the partitions that contains windows is.

---

### Post by FzZZy on 2008-01-05
/dev/sda5

i don't know where i can find any other info. I have only one physical disc. 4 partitions one swap ,root , home and ntfs for windows.

---

### Post by SOULRiDER on 2008-01-05
Just to make sure paste the output of this command
```
sudo fdisk -l
```

I believe what you should do is edit menu/lst
```
gksu gedit /boot/grub/menu.lst
```
and add this at the bottom
```
#Windows
title Windows
rootnoverify (hd0,4)
makeactive
chainloader +1
```

Then save and reboot.

---

### Post by FzZZy on 2008-01-05
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea18d094

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sda5               2        5099    40949653+   7  HPFS/NTFS
/dev/sda6            5100       12394    58597056   83  Linux
/dev/sda7           30280       30401      979933+  82  Linux swap / Solaris
/dev/sda8           12395       17257    39062016   83  Linux

---

### Post by FzZZy on 2008-01-05
I tried the things you wrote and it say that it is a invalid disk or some thing.

---

### Post by ajmorris on 2008-01-05
hi there fizzy, are you running grub, or grub2?

Also, can you post your /boot/grub/menu.lst file please?

---

### Post by SOULRiDER on 2008-01-05
Try this
```
title Windows XP
root (hd0,4)
savedefault
makeactive
chainloader +1
```

Tell us how it goes.

---

### Post by FzZZy on 2008-01-06
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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# kopt=root=UUID=d43818de-889a-4f56-9948-1b0bccfe3deb ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d43818de-889a-4f56-9948-1b0bccfe3deb ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d43818de-889a-4f56-9948-1b0bccfe3deb ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet
### END DEBIAN AUTOMAGIC KERNELS LIST
### WINDOWS
title Windows XP
root (hd0,4)
savedefault
makeactive
chainloader +1
### WINDOWS END
```

Testing this now.

---

### Post by FzZZy on 2008-01-06
it doesn't work i got error 12 : invalid device request

did the command geometry (hd0) in grub got this: 
(hd0,0)
(hd0,1)
(hd0,2)
(hd0,3)
(hd0,4) probably win xp type 0x7 unknown
(hd0,5) Ubuntu  type 0x83 ext3fs 
(hd0,6) swap type 0x82 unknown
(hd0,7) Ubuntu /home type 0x83 ext3fs
(hd0,8)

---

### Post by SOULRiDER on 2008-01-06
Try a 1 instead of a 0 in hd (0,4). I doubt it will work but youc an give it a go.

---

### Post by SOULRiDER on 2008-01-06
I just re-read your post and grub sais theres no NTFS partition, are you sure you didnt overwrite it or anything?

---

### Post by FzZZy on 2008-01-06
I had windows on d: and i formated c:. And i can access the windows drive in Ubuntu so all info is left on the d:. 

(hd1,4) didn't work

---

### Post by FzZZy on 2008-01-06
I have tried to use cfdisk to look att the partitions but i got an error.

bad primary partition 1: partition ends before sector 0

My be my partition table i messed up?
how do i fix that....reinstall Ubuntu?

---

### Post by SOULRiDER on 2008-01-06
Im sorry, but im rather lost too. Lets hope someone else can shed some light on this problem.

---

### Post by FzZZy on 2008-01-07
My theory now is that windowspartition isn't a primery partition. And threfore it can't boot. The outher theory is that windows had a booting thing on c: that i formated( windows folder is on d:).

---

