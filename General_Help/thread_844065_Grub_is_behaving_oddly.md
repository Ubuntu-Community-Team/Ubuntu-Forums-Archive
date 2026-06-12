---
title: "Grub is behaving oddly"
date: 2008-06-29
forum: General Help
---

### Post by DarkWinterNights on 2008-06-29
Good evening ladies and gentlemen.

I am presently running a dual-boot system with Vista and Hardy, and using the grub supplied with Ubuntu to access both.

Previously, I've had success with editing the /boot/grub/menu.lst file for altering the settings, but as of late this has proven ineffective.  I modified the headings in the grub (that is, the listing no longer indicates that Windows is an allowable selection from the grub - it has been deleted from the list for the time being), but the grub fails to reflect any of the chages.

I recall a while ago the automatic update saying something relating to updating the grub, and selecting that it should continue to use the same file I have been using previously, but now that I am trying to update the menu.lst file I can clearly see that the changes are not reflected in the grub's list itself.

Has anyone seen this kind of behaviour before?  There must still be a copy of the menu.lst file somewhere that the grub is referencing since it has retained my previous settings, but I cannot seem to locate it (I have searched the boot partitiion for any files relating to menu.lst, and although there are some Ubuntu example files that show up, none of them have the present grub data in them).

Any thoughts?

Thanks in advance.

---

### Post by rraj.be on 2008-06-29
> **DarkWinterNights said:**
> 
Previously, I've had success with editing the /boot/grub/menu.lst file for altering the settings, 
 There must still be a copy of the menu.lst file somewhere that the grub is referencing since it has retained my previous settings, but I cannot seem to locate it

There is no othere location your GRUB will reference for your menu.lst.
```

Make sure you have saved the edited menu.lst.
```

If you haven't saved it it may be useless to edit that.

Menu.lst can be only edited in sudo like this
```

sudo gedit /boot/grub/menu.lst
```

Further for managing GRUB booting you can use the following application

```
 sudo apt-get install startupmanager

```


This provides more options like

1--> setting default boot option.
2--> setting timeout
3-->Setting password for your GRUB
4-->customization of  your GRUB back ground

etc.

If you are not familiar with system and GRUB please avoid editing those.

If you want to edit the make a backup of your /boot/grub/menu.lst

---

### Post by VMC on 2008-06-29
> **DarkWinterNights said:**
> Good evening ladies and gentlemen.

... dual-boot system with Vista and Hardy, and using the grub supplied with Ubuntu to access both.

Previously, I've had success with editing the /boot/grub/menu.lst file for altering the settings, but as of late this has proven ineffective.  I modified the headings in the grub (that is, the listing no longer indicates that Windows is an allowable selection from the grub - it has been deleted from the list for the time being), but the grub fails to reflect any of the chages.

....

Do you recall exactly what you edited in menu.lst? That would be of help. Especially those headings. You have to be careful when modifying "#" and "##".

---

### Post by lswb on 2008-06-29
Do you really have a boot partition, or just a boot directory in the ubuntu partition? you can type "sudo fdisk -l" in a terminal to see how many partitions your system actually has. 

It is possible to have a /boot/grub partition and a /boot/grub directory on one or more other partitions, but only one /boot/grub/menu.lst file will be used to initially boot the system. Perhaps somehow this applies to you and you are editing the wrong /boot/grub/menu.lst

---

### Post by DarkWinterNights on 2008-06-30
The fields within menu.lst that I have altered previously had Windows Vista listed in the lists at the end of the file.  After altering the list, it now reads as follows:

> 
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=86f6a2bf-ca1a-4034-b5c9-d66cc5286e70 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=86f6a2bf-ca1a-4034-b5c9-d66cc5286e70 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet


Additionally, before I realized there was a problem with this, I had also changed the # prior to the hiddenmenu option at the beginning

> 
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu


I haven't changed the anything else in the file or rearranged the contents in any way beyond that.  Windows is located on (hd0,0), and is presently running a separate grub from that partition which I have since set as the boot partition, which, when loading the Ubuntu partition, triggers the second grub to trigger (the default Ubuntu grub).

I also notice that the timeout on the Ubuntu grub is no longer working either.

I am using sudo to edit the file and it is retaining the changes, but oddly not loading when using the grub itself.  I will give that startupmanager a try to see if that helps sort things out.

Also, I may not have correctly stated what I meant by boot partition.  What I had intended was that it was previously booting from the partition Ubuntu was stored on, whereas now it is booting from the Windows partition into the grub there which then boots the grub in the Ubuntu partition now.

I'll give it another whirl and get back to you all with becomes of me.  ;)  Thanks for some input.

---

### Post by DarkWinterNights on 2008-06-30
Having run startupmanager it gave me the option to install a newer version of the grub, which I accepted.  As it is written now, it displays

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
#hiddenmenu

# Pretty colours
#color cyan/blue blink-white/blue

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
# kopt=root=UUID=86f6a2bf-ca1a-4034-b5c9-d66cc5286e70 ro

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
# defoptions=splash quiet

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

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=86f6a2bf-ca1a-4034-b5c9-d66cc5286e70 ro splash quiet
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=86f6a2bf-ca1a-4034-b5c9-d66cc5286e70 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=86f6a2bf-ca1a-4034-b5c9-d66cc5286e70 ro splash quiet
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=86f6a2bf-ca1a-4034-b5c9-d66cc5286e70 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=86f6a2bf-ca1a-4034-b5c9-d66cc5286e70 ro splash quiet
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=86f6a2bf-ca1a-4034-b5c9-d66cc5286e70 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=86f6a2bf-ca1a-4034-b5c9-d66cc5286e70 ro splash quiet
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=86f6a2bf-ca1a-4034-b5c9-d66cc5286e70 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

However, upon bootup, the grub still shows the grub I had configured about a month ago. :(

---

### Post by DarkWinterNights on 2008-06-30
Also I guess I should add that the other grub on partition 0 is neoGrub installed through EasyBCD

---

### Post by VMC on 2008-06-30
So who's in control, Grub or some other boot loader?

When you turn of your PC does a text message appear saying grub stage 1.5 or something on that order?

---

### Post by caljohnsmith on 2008-06-30
Your description of your problem seems a bit confusing (at least for me), since for one thing you say you also use neogrub. Try going into the grub CLI (use "sudo grub"), and type "geometry (hd0)" to get a list of your partitions, and report the output. Then type "find /boot/grub/stage1" and also "find /grub/stage1" and see what those commands return; do you get more than one partition listed containing the stage1 file? Please also give the output of those commands and we can go from there.

---

### Post by DarkWinterNights on 2008-06-30
Right now, for convenience I have the neoGrub on partition 0 of hd0 (the windows partition) in control.  It indicates itself as "Windows Boot Loader" I believe it refers to itself.  When I select Ubuntu from the list, it then proceeds to boot into the Ubuntu grub (partition 2 of HD0).  From here, I can actually have it jump back to HD0 and load the first boot loader again, which is rather useless.  :P

grub geometry
> 
geometry (hd0)
drive 0x80: C/H/S = 38913/255/63, The number of sectors = 625142448, /dev/sda
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 1,  Filesystem type unknown, partition type 0x82
   Partition num: 2,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 3,  Filesystem type is ext2fs, partition type 0x83


Partition 0 is a NTFS partition with Vista on it.
Partition 1 is the swap.
Partition 2 is the Ubuntu partition
Partition 3 is storage, which at present is completely empty except for a folder called lost+found.

Find /boot/grub/stage1 indicates only that exact folder (/boot/grub/stage1) whereas find /boot/stage1 yields nothing at all.

> ~$ find /boot/grub/stage1
/boot/grub/stage1
~$ find /boot/stage1
find: /boot/stage1: No such file or directory


---

### Post by caljohnsmith on 2008-06-30
> **DarkWinterNights said:**
> Right now, for convenience I have the neoGrub on partition 0 of hd0 (the windows partition) in control.  It indicates itself as "Windows Boot Loader" I believe it refers to itself.  When I select Ubuntu from the list, it then proceeds to boot into the Ubuntu grub (partition 2 of HD0).  From here, I can actually have it jump back to HD0 and load the first boot loader again, which is rather useless.  :P

grub geometry


Partition 0 is a NTFS partition with Vista on it.
Partition 1 is the swap.
Partition 2 is the Ubuntu partition
Partition 3 is storage, which at present is completely empty except for a folder called lost+found.

Find /boot/grub/stage1 indicates only that exact folder (/boot/grub/stage1) whereas find /boot/stage1 yields nothing at all.
Just what exactly are you trying to accomplish? If neoGrub is in control of the MBR right now, you'll have to modify its configuration files if you want to change your boot menu options on start-up. If you want the MBR to instead point to your Ubuntu partition, and use the menu.lst in your Ubuntu partition on startup instead of neoGrub, then do the following in a terminal:
```
$ sudo grub
grub> find /boot/grub/menu.lst
[it should return (hd0,2), and if it does, then do:]
grub> root (hd0,2)
grub> install (hd0)
```

---

