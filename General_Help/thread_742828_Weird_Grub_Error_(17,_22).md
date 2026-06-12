---
title: "Weird Grub Error (17, 22)"
date: 2008-04-02
forum: General Help
---

### Post by dingorunner on 2008-04-02
Hello everyone and thank you all for your time.
I just re-installed Ubuntu 7.10 but Grub it's being weird, I mean, If I let my compurer boot normaly, it goes 
Grub Error 17, sometimes it's error 22, but if I insert Windows XP cd and restart, it goes:
"Press Any Key to Boot From CD" and then I wait a few seconds (without pressing any key) and the loads Grub normaly.

---

### Post by callkalpa on 2008-04-02
Try this .............


[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

---

### Post by dstew on 2008-04-02
The behavior of your system suggest that your BIOS is adding your CD-ROM drive to its list of drives when there is a CD in it, and since this was the way it was when grub was originally installed, grub gets the disk numbers right only if a CD is in there. If you don't boot the CD, apparently your BIOS goes to the next disk in line (your hard disk) and boots that, so you get grub. If the CD is in place, grub finds all its disks OK.

If the CD is not there, the BIOS numbers the hard disk partitions differently. Then, grub gets lost, so you get the error.

The way to fix this permanently is to edit the grub device.map file (/boot/grub/device.map) to tell grub what the true disk order is, despite what it is hearing from the BIOS.

Just to see what is going on, boot into Ubuntu like you did with the XP CD in place, and post the output of these commands:```
sudo fdisk -l
cat /boot/grub/menu.lst
cat /boot/grub/device.map
```Maybe we can figure out how to fix it.

---

### Post by dingorunner on 2008-04-02
Thanks for your answers. 
This is what I get :

[PHP]sudo fdisk -l
Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pistas, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Disk identifier: 0xe1a7e1a7

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        2678     1028160    f  W95 Ext'd (LBA)
/dev/sda3            2679        4591    15366172+  83  Linux
/dev/sda4            4592        9729    41270985    7  HPFS/NTFS
/dev/sda5            2551        2678     1028128+  82  Linux swap / Solaris

Disco /dev/sdb: 80.0 GB, 80000000000 bytes
255 cabezas, 63 sectores/pistas, 9726 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Disk identifier: 0x10ff10ff

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               2        9726    78116062+   f  W95 Ext'd (LBA)
/dev/sdb5               2        9726    78116031    7  HPFS/NTFS
[/PHP]

[PHP]cat /boot/grub/menu.lst
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
# kopt=root=UUID=2818bc53-e189-41c9-ba6b-54420619527a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=2818bc53-e189-41c9-ba6b-54420619527a ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=2818bc53-e189-41c9-ba6b-54420619527a ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
[/PHP]

[PHP]/boot/grub/device.map
(hd0)   /dev/sda
(hd1)   /dev/sdb
[/PHP]
Nevermind the PHP thing, I don't know how to use those tags.

As for Callkalpa's reply, I checked my bios and all devices were already on Auto Mode.

---

### Post by dstew on 2008-04-02
It looks correct, but obviously something is not working. We need to do some simple experiments. Do you get the grub error at the very start of the boot? That is, you get an error number with no explanation, correct? If so, it is a grub stage1.5 error, and it means that grub is not installed correctly. However, since it works properly with a CD in the drive, I don't think we can re-install grub from a boot that has a CD there. We need to boot the computer without a CD in the drive, and then re-install grub.

In my opinion, you should make a grub boot floppy, and boot from there (assuming you have a bootable floppy drive). You can make a grub boot floppy on any Ubuntu computer following the directions[ here]("https://help.ubuntu.com/community/GrubHowto/BootFloppy"). Once you have a grub boot floppy, you can boot into a grub command line, and do some simple experiments to figure out how to install grub onto your hard drive, so it will boot without the CD in there. If you want to try this, make the floppy, and post back once you can get the floppy to boot to a grub command line.

---

### Post by dingorunner on 2008-04-02
I actually re-installed Grub into my ubuntu drive (root, /dev/sda3), cause it also works if I insert a Ubuntu CD, I went Restore a broken system an reinstalled grub. The reason I use XP CD is because this CD gives me the option to press any key to boot from CD while Ubuntu's CD instantly boots itself.
PS: My floopy drive is broken.

---

### Post by dstew on 2008-04-02
So, does it work any different now since you re-installed grub? Anyway, without a floppy drive, I am pretty much out of ideas. Maybe having the CD in there is not to great a price to pay for a working system...

---

### Post by dingorunner on 2008-04-02
ok, my brother's gonna kill me but I'm using his floppy right now. I'm following the steps in order to make a boot floppy. It's taking for every though.

---

### Post by dingorunner on 2008-04-02
Everything was fine until this steps:

>  device (fd0) /dev/fd0
 root (fd0)
 setup (fd0)
 quit  

Error Message: syntax error near unexpected token 'fd0'

---

### Post by dingorunner on 2008-04-02
Ok I was skipping one step. Now let's assume I've got a working boot floppy. Now what did you have in mind, what kind of experiments do I need to carry on?

---

### Post by dstew on 2008-04-03
Boot it, without a CD in the CD-ROM drive. You should get a grub command line with the **grub>** prompt. That is where we enter the commands.

At the grub command prompt, type this:```
root (
```but do not press enter. Press the <TAB> key instead. This takes advantage of the auto-complete feature of grub to list the available disks. The first step it will tell you what disks you have available. Post that result. Then, put the disk name in, and press tab again, and it will give you a list of partitions, and their types (works kind of like fdisk, but uses grub names). Do this for all the disks it finds, and post the results.

---

### Post by dingorunner on 2008-04-03
OK I'll give it a try. 
As adional info, I tried booting into XP from de boot floppy but an error ocurred. Something about not finding 'THE' file.

---

### Post by dingorunner on 2008-04-03
This is what I got:

 ```

grub> boot (
Available disks: fd0  fd1 fd2 fd3 fd4 fd5 fd6 fd7 hd0 hd1
grub> boot(fd0) *Then I press TAB*
Error 1: Filename must be either an absolute path name or a blocklist.

```

---

### Post by dstew on 2008-04-03
OK, almost there. I guess **boot** will work just as well as **root**. But, to use the auto-complete to see the partitions, do not close the parenthesis. For (hd0), do it like this:```
root (hd0,
```Then press <TAB>. The (fd0) to (fd7) disks are floppies, and (hd0) and (hd1) are hard disks.

---

### Post by #Reistlehr- on 2008-04-03
you need to be careful when installing linux iin the very begining. If you have say, a USB drive in the USB port, and install on a IDE Harddrive, linux will read the HD as (hd1,0) and the USB as (hd0,0). If you remove it, the IDE drive will now be (hd0,0) and grub will look for (hd1,0). 

This is a known bug. Mostly exists because the USB drivers are read as SATA/SCSI drives to speed up compatability and such, and SDA takes precedence over IDE drives..

/dev/sdx = SCSI/SATA/USB
/dev/hdx = IDE drive

---

### Post by dingorunner on 2008-04-03
> **#Reistlehr- said:**
> you need to be careful when installing linux iin the very begining. If you have say, a USB drive in the USB port, and install on a IDE Harddrive, linux will read the HD as (hd1,0) and the USB as (hd0,0). If you remove it, the IDE drive will now be (hd0,0) and grub will look for (hd1,0). 

This is a known bug. Mostly exists because the USB drivers are read as SATA/SCSI drives to speed up compatability and such, and SDA takes precedence over IDE drives..

/dev/sdx = SCSI/SATA/USB
/dev/hdx = IDE drive


Thanks for yous reply. I don't think there was any device plugged in any USB port while I was installing Ubuntu if that's what you meant. 

Sorry, I WAS using root(...

---

### Post by dingorunner on 2008-04-03
Thanks for your help.
This is my 'feedback';

```
grub> root(
Available disks: fd0 fd1 fd2 fd3 fd4 fd5 fd6 fd7 hd0 hd1

grub> root (fd0,
Error 24: Attempt to access block outside partition

grub> root (fd1,
Error 25: Disk read error *same story for fd2 to fd7*

grub> root (hd0,
Possible partitions are:
Partition num 0 Filesystem type unknown, partition type 0x7
Partition num 2 Filesystem type is ext2fs, partition type 0x7
Partition num 3 Filesystem type unknown, partition type 0x7
Partition num 4 Filesystem type unknown, partition type 0x82

grub> root (hd1, [I]automatically fills with 
grub> root (hd1,4) [/I]
```

---

### Post by dingorunner on 2008-04-04
Thanks a lot dstew. I fixed the problem!. I repaired MRD from Windows XP CD, and then booted from Ubuntu CD and reinstalled Grub on hd0. My mistake was that I didn't install Grub on hd0. Anyways thanks.

---

