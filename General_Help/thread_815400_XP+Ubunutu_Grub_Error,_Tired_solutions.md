---
title: "XP+Ubunutu Grub Error, Tired solutions"
date: 2008-06-01
forum: General Help
---

### Post by pilate on 2008-06-01
I think I know what caused this problem. I just don't know how to fix it. I recently installed Ubuntu on a machine which already had XP. That machine is a Dell Vostro 1500 btw. Every thing worked fine. I had an early version of Ubuntu already on the machine so I already had a partition set aside for the new version.
Install went great. But I needed to get some work done and went back to my windows for a few days (I'm still learning linux).
Well today I decided to do a disk defragment on my laptop. I download a program called UltraFrag. It has an option to start on next boot. So I selected that (done in windows).
When I started my computer over I got a Error 17 in Grub.
I've read some things on the forums about it and they haven't helped much yet. 
I only have 1 drive so it's not my bios reading it wrong. 
I changed menu.lst to include rootnoverify for the XP boot instead of just root, but that didn't do anything.
I tried installing SuperGrubDisk on a usb drive but when I try to run the command grub> root (hd3,0) is says something about the drive having to many cylinders for the BIOS.

So now I'm stuck. I know UltraFrag just put a hook in somewhere that Grub doesn't like, but I don't know how to get it out, or even where to look.
Thanks for the help.

---

### Post by didac on 2008-06-02
Having too many cylinders is not a problem.

Boot and press any key to enter the GRUB menu. Chose C for a command prompt. There type:

```
find /boot/grub/stage2
```

It will tell you where your grub root is. Then:

```
root (hd3,0)
```

change hd3,0 for whatever find told you.

```
kernel /boot/vmlinuz (give a tab for autocompletion) root=/dev/sdc1 ro
```

Now, the root=/dev/sdc1 is the tricky part. If your root is hd3,0, the normal thing would be for the filesystem to be in sdc1, but isn't always like that.

```
initrd /boot/initrd (give a tab)
boot (and ENTER)
```


You should be going by now. Once it boots, do

```
sudo gedit /boot/grub/menu.lst
```

Write the root, kernel parameters you entered manually at the command.


IF THIS IS TOO CONFUSING: boot with a live-CD. Do

```
sudo fdisk -l
```

Post the result here. Try to find in which partition you have /boot/grub/menu.lst and post it too. Post also /etc/fstab. Partitions should be in /media. Don't post what comes with the liveCD. It should be something like /media/sdc1/boot/grub/menu.lst and not /boot/grub/media.lst

Hope it helps and you aren't dizzy by now.

---

### Post by pilate on 2008-06-02
Ok I went with the livecd option because I'm not able to get grub to come up during boot long enough to press any key.

fdisk -l results
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      104391   de  Dell Utility
/dev/sda2   *          14        3208    25663837+   7  HPFS/NTFS
/dev/sda3            3209       19457   130520092+   f  W95 Ext'd (LBA)
/dev/sda5            3209       13986    86574253+   7  HPFS/NTFS
/dev/sda6           13987       14811     6626781   83  Linux
/dev/sda7           14812       18680    31077711   83  Linux
/dev/sda8           18681       18852     1381558+  82  Linux swap / Solaris
/dev/sda9           18853       19131     2241036   82  Linux swap / Solaris
/dev/sda10          19132       19457     2618563+  dd  Unknown

```

I'm pretty sure my Ubuntu partition is 7, but I'm not sure. Here's menu.lst
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
default		7

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
# kopt=root=UUID=1fa14942-c8cd-4187-b875-ede801dbde65 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,8)

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

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=1fa14942-c8cd-4187-b875-ede801dbde65 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=1fa14942-c8cd-4187-b875-ede801dbde65 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1fa14942-c8cd-4187-b875-ede801dbde65 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1fa14942-c8cd-4187-b875-ede801dbde65 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,8)
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
title		Microsoft Windows XP Home Edition
rootnoverify		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=26f15b69-22d7-45fa-9057-2840a28d15d0 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=26f15b69-22d7-45fa-9057-2840a28d15d0 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 7.10, memtest86+ (on /dev/sda6)
root		(hd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda8
title		Microsoft Windows XP Embedded
root		(hd0,7)
savedefault
makeactive
chainloader	+1

```

and here's fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=1fa14942-c8cd-4187-b875-ede801dbde65 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda10
UUID=4ee7148a-8567-480f-a43a-c4427c3952a8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

The only thing that shows up when I mount the disk and find menu.lst is /media/disk/boot/grub.

---

### Post by meierfra. on 2008-06-03
It looks like that your partition table used to be not in the physical order  and  somebody (maybe  defrag) fixed that for your. So now the grub setting are all wrong.

Try this: Boot from the LiveCD, 


```
sudo grub
```

and at the grub prompt:

```

find /boot/grub/stage2
```

The output will "(hd0,6)" if ubuntu is really on /dev/sda7

Then (still at the grub prompt)

```
root (hd0,6)  #  use the output from the previous command
setup (hd0)    
quit

```

You also need to edit "menu.lst"

Change all (hd0,8[SIZE="1"] [/SIZE]) to (hd0,6)  (of course use the output of "find ..")

Don't forget to change "#groot (hd0,8[SIZE="1"] [/SIZE])"

Save the file and hope for the  best.

---

### Post by pilate on 2008-06-03
That worked perfectly. Thank you both for your help.

---

