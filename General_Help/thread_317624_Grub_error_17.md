---
title: "Grub error 17"
date: 2006-12-12
forum: General Help
---

### Post by v8YKxgHe on 2006-12-12
Hey,

I am getting Grub error 17 when I plug in my spare, storage dump FAT32 hard drive, here is my hard drive setup:

1x SATA-2 with Ubuntu installed
1x IDE hard drive, formated as FAT32

If I disconnect the IDE hard drive, Ubuntu will boot fine - yet if I connect the IDE hard drive I get Grub error 17.

The IDE hard drive used to have Ubuntu on it, but I then formated that with PartitionMagic8 in Windows. My guess is the IDE hard drive still has GRUB installed on the MBR somewhere and causing some conflict.

I did not have the IDE hard drive connected when I installed Ubuntu ( _all_ of my important files are on the IDE hard drive, I can't afford Ubuntu to mess it up or I select the wrong hard drive to format by accident, so I leave it disconnected ).

Does anyone know how to fix this error 17?

---

### Post by Sef on 2006-12-12
From Gentoo's error collection:

> 5. Grub Error 17

Situation

Code Listing 5.1: Grub Output

root (hd0,0)
filesystem type unknown partition type 0x7

Error 17 : Cannot mount selected partition

Solution

This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

Be sure to check your root(x,y) settings in your grub.conf.

Also, if you are trying to boot Windows, make sure that your grub.conf file has the root (hdX,Y) (or rootnoverify (hdX,Y)) and chainloader (hdX,Y)+1 in it. 

---

### Post by ~LoKe on 2006-12-12
An example of mine:
> title           Ubuntu, kernel 2.6.19-7-generic
**root            (hd1,0)**
kernel          /boot/vmlinuz-2.6.19-7-generic root=UUID=6ce76683-93e6-41db-86b9-93b37cf31bdb ro quiet splash
initrd          /boot/initrd.img-2.6.19-7-generic
savedefault

What you would do is modify the grub menu to boot hd1,0.  If that doesn't work, try hd2,0 or hd0,1 etc.

---

### Post by v8YKxgHe on 2006-12-13
Hum that still doesn't work. I've tried hd1-9,0 yet non of those work. 0 is the only one that will work, but then when it comes to the Ubuntu loading screen it just doesn't load at all.

I've tried all different combinations but non of them work. Would getting an WinXP disc and fixing the MBR/creating a new windows MBM work? I'll go try it now!

---

### Post by v8YKxgHe on 2006-12-13
Nope that doesn't work...... I'm confused :confused:

---

### Post by v8YKxgHe on 2006-12-13
Weird, even if I load the LiveCD it get's stuck when loading Ubuntu. What could be wrong with my IDE Hard drive? If I disconnect it everything works fine, :confused: ](*,)

---

### Post by v8YKxgHe on 2006-12-13
Ok, wtf. I've just tried 3 different IDE hard drives and they all make Ubuntu lock up when it goes to boot. How can that be?!

---

### Post by v8YKxgHe on 2006-12-13
I just started Ubuntu in recovery mode and I get this output:

end_request: I/O error, dev sda, sector 8
Buffer I/O error on device sda, sector 24

I get a load of them, could someone help?

---

### Post by bulldog on 2006-12-13
Can you give the outcome of ```
sudo fdisk -l (l as in like)
```
And a copy of your menu.lst would be nice too.
```
gksudo gedit /boot/grub/menu.lst
```

The reason for your trouble is most likely,your both drives IDE and SATA are masters.

---

### Post by v8YKxgHe on 2006-12-13
Ahhhhhhhhhhhhhhhhhhhhhh yes, my IDE hard drive is set to Master and my CD Drive is set to slave.

I'm not home at the moment, but when I get home I shall try what you said, but I will first try setting my IDE hard drive to Slave then my CD Drive to Master, do you think that would work?

---

### Post by v8YKxgHe on 2006-12-13
Setting the IDE hard drive to Slave and the CD Drive to Master still did not work. It just gets to the boot splash and locks up.

Here is the output of fdisk -l

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14216   114189988+  83  Linux
/dev/sda2           14217       14593     3028252+   5  Extended
/dev/sda5           14217       14593     3028221   82  Linux swap / Solaris

```

That is without the IDE hard drive connected ( as obviously I can't boot into Edgy to do that with it connected )

And here is the menu.list

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
# kopt=root=UUID=d61526ff-7e20-4df6-9f69-da57f66f1e6a ro
# kopt_2_6=root=/dev/sda1 ro

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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by igknighted on 2006-12-13
Hmm, its a long shot but try this:

1) check your bios settings to make sure it is booting from the proper disk
2) try setting both the HD and CD drive to Cable Select
3) try putting the optical and hard disks on seperate IDE channels if you can
4) if none of that works, try removing the IDE drive from your fstab so it doesn't try to mount it and see if that makes a difference.

I googled that particular error and it seems that it is caused by an unrecognized file system... try reading this thread, its from the Gentoo forums, but grub is grub, so the suggestions might work: [http://forums.gentoo.org/viewtopic.php?t=120802](http://forums.gentoo.org/viewtopic.php?t=120802)

One more thought: for like 15 or 20$ US you can pick up a case for that HD so you can turn it into an external and connect via USB... if all else fails you could do that, with the side benefit of having a portable harddrive

---

### Post by v8YKxgHe on 2006-12-13
I will try setting them to cable select now. I can't put the CD Drive and IDE hard drive on seperate IDE channels as the motherboard only has 1 IDE connector. 

You said remove it from fstab, where is that? - I'll check that link out now, the IDE hard drive is FAT32 ( So I can easily transfer files between Windows and Linux ).

---

### Post by igknighted on 2006-12-13
There should be a line in the file /etc/fstab that tells Ubuntu where to mount the drive and other info about it.  If you remove this line perhaps it wont try to deal with it on boot, but you would have to mount it manually later on when you want to use it.

---

### Post by v8YKxgHe on 2006-12-13
Hum, well the IDE hard drive is not listed in fstab - that's probably because I didn't have it connected when I installed Ubuntu. Like said before, if I connect it I can't even boot the liveCD to install Ubuntu - it just doesn't like IDE and SATA =(

---

### Post by igknighted on 2006-12-13
That's really odd... I have 2 IDE drives and an SATA drive in my box and it boots just fine... lets try the opposite then... try adding this line to your fstab file to tell it what it is:
```
/dev/hda1            /media/fat32              vfat       defaults                    0 0
```

you will have to create that file (/media/fat32) before it will mount it there.

EDIT: I totally forgot, I think there is something special that goes on the end of that fstab line for fat32 drives but I can't for the life of me remember what it is...

---

### Post by v8YKxgHe on 2006-12-13
:( nope that doesn't work either. When it gets to the Ubuntu splash I get no hard drive activity from my SATA hard drive ( which has Ubuntu installed ) but I get a little bit of activity from my IDE Hard drive. Then after a while my CD Drive makes a noise like a blimming floppy drive! very weird!

---

### Post by igknighted on 2006-12-13
One last thought... what if you tried downloading the gparted liveCD (or the liveCD from any other distro, Sabayon 3.2 mini would be a great choice) and tried to boot that liveCD with the second HD in.  If you can get it booted it could be a faulty Ubuntu disk that lead to a faulty grub loader as well.

---

### Post by v8YKxgHe on 2006-12-13
well it boots, but it never finds the drives. Just sits there scanning for them. 

Why does nothing I have ever work *cries*

---

