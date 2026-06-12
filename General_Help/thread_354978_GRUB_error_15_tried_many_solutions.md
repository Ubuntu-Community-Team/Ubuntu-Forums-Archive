---
title: "GRUB error 15: tried many solutions"
date: 2007-02-06
forum: General Help
---

### Post by raul_ on 2007-02-06
I had my linux drive as sda6 but i removed a partition (sda5) and now my linux partition is sda5. So i went and edited fstab and put it like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

/dev/**sda5** / ext3 defaults,noatime,errors=remount-ro,data=writeback 0 1
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb        /media/usb0     auto    rw,user,noauto  0       0
#/dev/sda1    /media/windows_c    ntfs-3g    defaults,locale=pt_PT.utf8    0 0
/swapfile       none    swap    sw      0 0
/dev/**sda6**       /home   ext3    nodev,nosuid    0 2

```

i changed the words in bold. subtracted a number to them. Then i changed my menu.lst file to make grub look for the right device to boot. The changes are also in bold (also minus 1):

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry# (normally the first entry defined).
timeout         5

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
# kopt=root=UUID=31d17169-3b75-4065-be77-3623650903de ro quiet

## default grub root device
## e.g. groot=(hd0,0)
# **groot=(hd0,4)**

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
# defoptions=splash rootflags=data=writeback elevator=cfq

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single rootflags=data=writeback

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

splashimage=(hd0,4)/boot/grub/splash.xpm.gz

title           Ubuntu, kernel 2.6.17-10-386
root            **(hd0,4)**
kernel          /boot/vmlinuz-2.6.17-10-386 root=UUID=31d17169-3b75-4065-be77-3623650903de ro quiet splash rootflags=data=writeback elevator=cfq
initrd          /boot/initrd.img-2.6.17-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root            **(hd0,4)**
kernel          /boot/vmlinuz-2.6.17-10-386 root=UUID=31d17169-3b75-4065-be77-3623650903de ro quiet single rootflags=data=writeback
initrd          /boot/initrd.img-2.6.17-10-386
boot

(.......changed every old kernel too.....)

title           Ubuntu, memtest86+
root            (hd0,4)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

Heres is my fdisk -l output too:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4343    34885116    7  HPFS/NTFS
/dev/sda2            4344       14593    82333125    f  W95 Ext'd (LBA)
/dev/sda5   *        4344        7530    25599546   83  Linux
/dev/sda6            7531       14593    56733516   83  Linux

```

I already tried reinstalling grub from the live cd:
```

sudo grub
root (hd0,4)
setup (hd0)

```

Now i don't get nothing, not even error 15. All i get is some kind of smile (??) near the lower right corner
 What did I do wrong? :(

---

### Post by bodhi.zazen on 2007-02-06
See if this helps:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#15](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#15)

I would boot to the live CD and mount your partitions ...

First make sure the uuid did not change. second make sure your partitions are numbered properly, is /dev/sda6 actually your root partition ?

HTH

---

### Post by raul_ on 2007-02-06
Everything is correct, including UUID. But now i don't even get to the error. As i said i get a strange character that looks like a smile =\

---

### Post by bodhi.zazen on 2007-02-06
Sorry but to a casual review I do not see any problems ...

Perhaps try:

1. Boot to recovery mode ?

2. boot without these options : rootflags=data=writeback elevator=cfq

3. re-install grub, from the live cd:```
sudo grub
root (hd0,4)
setup (hd0,4)
setup (hd0)
quit
```

---

### Post by raul_ on 2007-02-06
Yes i did that again, but as I said, now I dont even get to "Grub loading" . my screen is completely blank and then i see some "_" flying here and there, and im stuck with a smile in the bottom of my screen.

---

### Post by Jimmy_r on 2007-02-06
> **raul_ said:**
> im stuck with a smile in the bottom of my screen.

LOL... The first Grub virus?
Sorry, this just seems very odd... Have no idea :confused:

---

### Post by raul_ on 2007-02-06
Here is a photo of the error.. Sorry for the crappy quality. I tried the Super Grub disk, tried to install it again automatically and manually but nothing...

---

### Post by bodhi.zazen on 2007-02-06
Hardware failure ?

Can you boot from supergrub ???

---

### Post by raul_ on 2007-02-06
Yes, I can boot from SuperGrub. I'm running the Dapper Live CD now

---

### Post by raul_ on 2007-02-06
UPDATE: Well i tried the Grub Super Disk again and tried to boot from the MBR and IT WORKS!!. At least i'm in my desktop again. I guess this isn't a GRUB error anymore so i guess i should start another thread?

---

### Post by raul_ on 2007-02-06
check [http://www.ubuntuforums.org/showthread.php?p=2116398]("http://www.ubuntuforums.org/showthread.php?p=2116398")

Please continue discussion there :)

---

