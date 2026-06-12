---
title: "after ubuntu install, vista boot failes"
date: 2006-11-16
forum: General Help
---

### Post by GaryG007 on 2006-11-16
I had Vista installed on my "play" puter.  Installed Ubuntu (just downloaded it) using most of the defaults.  It re-arrainged my single 80G harddrive, left vista intact and ubuntu installed clean.
Grub splash screen shows some ubuntu options, it also shows vista.
Ubuntu boots fine. If I select vista the boot hangs.  Tried to boot vista in safe mode and the last thing the log shows is "/windows/system32/drivers/crcdisk.sys"

Vista booted ok before I installed ubuntu

Any idea what is going on

Gary

[email]gwgrover@windstream.net[/email]

---

### Post by nova- on 2006-11-16
Hi!

post your ubuntu's /boot/grub/menu.lst :
sudo cat /boot/grub/menu.lst

and post the result of this command in ubuntu:
df -Th

---

### Post by GaryG007 on 2006-11-16
Thank you for the reply, Nova

hopefully the meun.lst got attached; 

*_here is the result of the df -Th command._*
clyde@clyde-desktop:~$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/hdc3     ext3     14G  1.9G   12G  14% /
varrun       tmpfs    506M   80K  506M   1% /var/run
varlock      tmpfs    506M     0  506M   0% /var/lock
procbususb   usbfs     10M  108K  9.9M   2% /proc/bus/usb
udev         tmpfs     10M  108K  9.9M   2% /dev
devshm       tmpfs    506M     0  506M   0% /dev/shm
lrm          tmpfs    506M   18M  489M   4% /lib/modules/2.6.17-10-generic/volatile
clyde@clyde-desktop:~$

---

### Post by GaryG007 on 2006-11-16
well, I don't see the 'attach' so I'll paste it :

clyde@clyde-desktop:~$ sudo cat /boot/grub/menu.lst
Password:
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
# kopt=root=UUID=2024ea53-ffd3-483a-8cd2-0603a8fc3efc ro
# kopt_2_6=root=/dev/hdc3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# defoptions=quiet splash noapci nolapci

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

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

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdc3 ro quiet splash noapci nolapci
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdc3 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1

clyde@clyde-desktop:~$ 
clyde@clyde-desktop:~$

---

### Post by GaryG007 on 2006-11-16
Just for grins, here is the fdisk list:

clyde@clyde-desktop:~$ sudo fdisk -l

Disk /dev/hdc: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        2929    23527161    7  HPFS/NTFS
/dev/hdc2            4865        9733    39110242+   7  HPFS/NTFS
/dev/hdc3            2930        4781    14876190   83  Linux
/dev/hdc4            4782        4864      666697+   5  Extended
/dev/hdc5            4782        4864      666666   82  Linux swap / Solaris

Partition table entries are not in disk order
clyde@clyde-desktop:~$

---

### Post by bernied on 2006-11-16
> If I select vista the boot hangs. Tried to boot vista in safe mode and the last thing the log shows is "/windows/system32/drivers/crcdisk.sys"
... implying that windows is actually booting - the option to boot windows in safe mode is part of windows, not grub. This is some new vista wierdness that we have to learn about no doubt. Thankfully I've not had the pleasure of the acquaintance - and hope to avoid it a while longer.

---

### Post by bernied on 2006-11-16
windows was probably using that space between hdc1 and hdc2, maybe you've toasted its recovery partition or something - what is that first linux partition - your boot partition?

---

### Post by bernied on 2006-11-16
if it were mine I'd try their nasty recovery cd, but be ready for it to kill your linux.

---

### Post by bernied on 2006-11-16
sorry, wasn't paying attention - that's your root partition

---

### Post by bernied on 2006-11-16
Have you seen this thread? -
[http://forums.microsoft.com/TechNet/ShowPost.aspx?PostID=543600&SiteID=17](http://forums.microsoft.com/TechNet/ShowPost.aspx?PostID=543600&SiteID=17)

---

### Post by GaryG007 on 2006-11-17
Thank you all for the responces; but I thing there are some may be some hardware issues

---

