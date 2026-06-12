---
title: "Boots to BusyBox instead."
date: 2008-01-28
forum: General Help
---

### Post by JNic on 2008-01-28
As this question will most likely show, I am fairly new to the Linux community.  Anyways, I have been running a dual-boot with XP and Ubuntu fine until recently.  This past weekend I did some tidying up in the inside of my computer and moved some things around. 
     Alright, my motherboard has an IDE 1, 2, and 3.  Before this problem, my partitioned hard drive resided on IDE 1 as master with its jumper set to master and my CDRom as a slave on IDE 1.  Now, I have moved the CDRom to master on IDE1 with its jumper set to master.  I have put the hard drive on IDE 2 as master with its jumper removed as says its directions when it is the only device on a channel.  Whenever the system boots, the GRUB menu is shown and XP can be booted fine but whenever any of the Ubuntu options are selected it seems like it attempts to boot but then loads the BusyBox.
     I apologize for such a long description but I felt it was needed to ask my question which is how can I get Ubuntu booting again?  Thank you in advance and if anymore system specs are required then I will gladly supply them.

---

### Post by tgilber1 on 2008-01-28
It sounds like you may have root pointing to the wrong location. Please, provide the contents of your menu.lst.  Also, when you boot up, try the following:

1.  At the GRUB menu, press the ESC key
2.  Press the 'c' key to get to the GRUB interactive interface
3.  From the GRUB prompt, type "find /grub/menu.lst" (omit quotes)
4.  Make sure that root is pointed to the correct device in your grub menu for root and kernel line.

title           Ubuntu 7.10, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.20-16-generic root=/dev/sda1 ro quiet
initrd          /initrd.img-2.6.20-16-generic
quiet

---

### Post by JNic on 2008-01-28
Thank you for your reply tgilber1.  Here is where I stand now.  From the Grub menu I pressed 'c' and entered the GRUB interactive interface.  But upon entering your 'find' command (pointing to '/grub/menu.lst') it said it was unable to find the file.  But, when i ran 'find /boot/grub/menu.lst' it was able to find the file.  I would guess that this is not the file you are speaking of because it only returns one line which is '(hd0,2)' and that is it.  See, I am having to continually boot into XP to type these but if I remember correctly, if i pressed 'e' on the first Ubuntu entry that it also said '(hd0,2)'.  Not sure if that will help.  And am looking forward to more help from you.  Thanks

---

### Post by JNic on 2008-01-28
Alright, update.  I was able to view the menu.lst file through XP and this is it contained.  Quite confusing if you ask me.  I hope you will be able to decipher it. Thanks again.


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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

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
# kopt=root=UUID=c8ac16fe-fe6c-44cc-a751-8c0d425e4852 ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c8ac16fe-fe6c-44cc-a751-8c0d425e4852 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c8ac16fe-fe6c-44cc-a751-8c0d425e4852 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=c8ac16fe-fe6c-44cc-a751-8c0d425e4852 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=c8ac16fe-fe6c-44cc-a751-8c0d425e4852 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by tgilber1 on 2008-01-29
Sorry for the error with the /grub/menu.lst.  On my machine, I have the /boot as its own partition.  Hence, I issue a find /grub/menu.lst.  If you have the root and boot directories on the same partition, then I believe you have to issue the find /boot/grub/menu.lst.

In any event, your grub menu is pointed to the correct partition.  Try the following steps to make sure you image file exists

1.  Boot up computer
2.  At GRUB menu, press the ESC key
3.  Press 'c' key to access GRUB interface
4.  Type "root (hd0,2)" omitting the quotes
5.  Type "kernel /", then press tab key to finish command.  At this point, you should see available files on the root partition, i.e., the backslash '/' is the root directory.
6.  Make sure you have your image files

_Example files are below_
System.map-2.6.22-14-generic
vmlinuz-2.6.22-14-generic
initrd.img-2.6.22-14-generic

7.  If files are missing, you need to create image files with the update-initramfs command.  If files do exists, then you may have a missing module that is not recognizing your hard drives when you boot up.

---

### Post by JNic on 2008-01-29
I would like to thank you once again tgilber1 for your time and the help you have given me thus far.  But unfortunately this problem will go unsolved.  Read on if you want to know why.  
             I performed the actions you suggested in your last post but it did return the files you mentioned so this was not my problem, so I think.  So I was left there again scratching my head wondering what it would take to get linux running again.  So, I weighed my options and convinced myself that a reinstall of ubuntu was in suit  I really hadn't done terribly too much on that installation and was pretty sure that a fresh install would allow me to begin using it again.  So, since the current ubuntu installation was now considered obsolete, to me at least,  it was my bright idea to just delete its partition and then reformat and install it once more.  And so I did.  All seemed fine until I restarted my PC and it got no further than the end of the POST and then halted claiming it couldn't find Grub, duh, of course it  can't now.  So now not only can I not boot into ubuntu but I am also locked out of XP.  So, upon research I learned that if I could rewrite the MBR(?) code then it would boot fine.  But not only could I not get the command to run form the 98 disc but also not from the rescue option on the XP disc.  But, to make a long story short, or at least shorter, I got hold of an app that I was able to use to fix the partition tables and write the MBR code.  As a matter of fact I am typing on this particular PC right now.

---

