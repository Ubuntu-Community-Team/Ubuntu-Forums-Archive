---
title: "Windows Vista Won't Load"
date: 2008-03-15
forum: General Help
---

### Post by jackdelamare on 2008-03-15
Hello,

I just installed Ubuntu as a partition on my Lenovo laptop. Before this, Windows Vista was working fine on there.

Now, whenever I start up, I get these options:

Ubuntu 7.10, kernel 2.6.22-14-generic
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
Ubuntu 7.10, memtest86+
Other operating systems:
Windows Vista/Longhorn (loader)
Windows Vista/Longhorn (loader)

But when I click Windows Vista, it does not load correctly. It comes up with "Windows is loading files", then goes to the green loading bar, and then goes to "Rescue and Recovery 4", which was on the computer originally.

Please help, I don't want to loose my Vista but I still want Ubuntu.

Thanks.

---

### Post by Amarsingh0793 on 2008-03-15
Did you manually configure your partitions in the Live CD using the installer? Or did you use the Guided Partitioner? 

You should remember that when you resize partitions, you should backup your data!

---

### Post by jackdelamare on 2008-03-15
I manually configured the partitions using Gnome since GParted wouldn't work.

---

### Post by forrestcupp on 2008-03-15
post the results of 
```
sudo fdisk -l
```
and the contents of
```
gksu gedit /boot/grub/menu.lst
```

If you didn't screw up your Vista partition, it's a problem with grub's menu.lst.

---

### Post by jackdelamare on 2008-03-15
Ok, i'll check those out... where do I find them? I new to all of this.

---

### Post by forrestcupp on 2008-03-15
> **jackdelamare said:**
> Ok, i'll check those out... where do I find them? I new to all of this.

just open up a terminal and type the commands I gave you.  The first one will give an output in the terminal, thich you should copy and paste into your post.  The 2nd one will open up a file in a text editor, which you should copy and paste in your post.

To get to your terminal, go to main menu->Accessories->Terminal.

---

### Post by jackdelamare on 2008-03-16
First:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         708     5684224   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         709       18182   140359905    7  HPFS/NTFS
/dev/sda3           18183       19457    10241437+  83  Linux
```

Second:
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
# kopt=root=UUID=7e096ea9-06db-4089-8d69-22604bc586a1 ro

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
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7e096ea9-06db-4089-8d69-22604bc586a1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7e096ea9-06db-4089-8d69-22604bc586a1 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

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
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

---

### Post by justleen on 2008-03-16
do both Vista option fail?

looking at you output above, the second Vista points to the right place..

---

### Post by jackdelamare on 2008-03-16
Both of them fail yes. How do I fix this?

---

### Post by forrestcupp on 2008-03-17
It looks to me like the 2nd Vista option should be the right one.  It appears that the 1st option for Vista in your grub menu is probably for your recovery partition.  The 2nd Vista option should be for your actual Vista install.  So you should probably make sure to choose the 2nd option for Vista and see what it does.  

Does choosing the 2nd Vista option take you to the recovery also?  If not, what does it do?

---

### Post by jackdelamare on 2008-03-17
It takes me to exactly the same as number 1, Rescue and Recovery.

---

### Post by jackdelamare on 2008-03-20
So yeah, know anything to help me load Windows Vista?

---

### Post by jackdelamare on 2008-03-22
Hello, is there anybody that could help with this? I sortof need to use Vista on my laptop.

---

### Post by jackdelamare on 2008-03-28
Since Ubuntu has just given me problems I was wondering, if I uninstall Ubuntu, will my Windows Vista work again?

---

### Post by heartburnkid on 2008-03-28
Probably not; you'd likely have to reinstall Vista in order to get the boot loader back if you uninstalled Ubuntu.

That is strange; I'm no GRUB expert, but it does look like GRUB should be pointing to two separate partitions there...  Likely, this is causing problems because your OEM uses a proprietary program to enable their "restore partition", and said program doesn't play nice with GRUB.  I've got an idea of what you might do, but I make no guarantees that it won't break things further:

Run the following two commands from the terminal:

```
gksu cp /boot/grub/menu.lst /boot/grub/menu.bak
gksu gedit /boot/grub/menu.lst
```

And remove the first Vista section (i.e. this bit I've quoted below):

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

Save, then reboot.  There should now be just one Vista entry; try it and report back on what happens.

If you can't boot at all after this, then start from the Ubuntu LiveCD, go back to the terminal and enter:

```
gksu cp /boot/grub/menu.bak /boot/grub/menu.lst
```

This should restore your configuration.

---

### Post by jackdelamare on 2008-03-28
There now is only 1 boot of Windows Vista BUT it still goes to Rescue and Recovery. What should I do?

---

### Post by stchman on 2008-03-28
I know that hindsight is 20/20, but NTFS get fragmented pretty quickly in Windows.

IN the future make sure you do a defrag and a chkdsk /f on all NTFS partitions BEFORE resizing them.

What will happen is that files will get fragmented all over the place and the NTFS journal can be compromised.

My recommendation is to:

1.  Get the data off of the Vista partition you need and save it.
2.  Completely wipe the drive.
3.  Reinstall Vista with an option to use only part of the drive.  Make sure to leave some FREE SPACE for Ubuntu.
4.  Immediately after Vista install install Ubuntu.  Tell Ubuntu to use the largest available free space.

After installation of both OSs then install appropriate drivers for Vista.

I would also recommend that you get you hands if possible on an OEM Vista DVD and use your key on the bottom of your laptop.  This way you are legal.

The OEM DVDs of Vista do not have all the trial cr@pware.

---

### Post by jackdelamare on 2008-03-28
I am angry now, I did defragment and everything looked clean. So I've lost my Windows Vista? How great.
I used an OEM version of Windows Vista on my desktop PC, so, to save myself buying another one, should I use that CD in my laptop and use the product key on the bottom of my laptop? Would that work?
I also had some Lenovo software on there which allow the fingerprint login and webcam to work, so I'd loose all that?
Wow, Ubuntu just screws up my computer.

---

### Post by heartburnkid on 2008-03-28
> **jackdelamare said:**
> I am angry now, I did defragment and everything looked clean. So I've lost my Windows Vista? How great.
I used an OEM version of Windows Vista on my desktop PC, so, to save myself buying another one, should I use that CD in my laptop and use the product key on the bottom of my laptop? Would that work?
I also had some Lenovo software on there which allow the fingerprint login and webcam to work, so I'd loose all that?
Wow, Ubuntu just screws up my computer.

Blame your OEM for using proprietary boot software.  Ubuntu and Vista generally play very nicely together.

---

### Post by lswest on 2008-03-28
Okay, so you're saying you want to get rid of Ubuntu?  do so, then to restore the windows bootloader do this:
boot to the recovery partition
get to a recovery console (it should be easy enough to find)
run these:
```
bootrec /fixmbr
bootrec /fixboot

``` and if it still doesn't boot do:
```
chkdsk /f
``` which should fix your windows partition.  Sorry to hear your ubuntu experience wasn't what you expected.  Maybe try Hardy at a later date?

also, the partition he wants to boot to is sda1 so it should be: root (hd0,1)

also, the recovery partition should give you the option to re-install Vista with everything you had before, the way you got it from your supplier, then you can resize for ubuntu, or leave it.

by the way, i know for a fact Vista and Ubuntu play very well together, i have both running on my laptop, i even had an XP/Vista/Ubuntu triple boot before, so if there's a problem it's not caused by Ubuntu.

---

### Post by jackdelamare on 2008-03-28
Hopefully that'll work but I deleted the first Vista as shown above, and that was sda1. How do I get that back, to do all of this?
And how do I boot to the recovery partition?

EDIT: I got sda1 back so now there's 2 Vista. Now how do I boot to the recovery partition thing?

---

### Post by lswest on 2008-03-28
you should be able to get to the recovery partition through the first entry (the one that reads root (hd0,0)) and then from there, i'm not sure, never seen the recovery system of a Lenovo notebook, but it would probably have a recovery console option under advanced or so, or else try to boot to the other vista, and hit "F8" before it starts loading, which should give you a command prompt option.

If you can't find the right console, give a list of options the recovery partition gives you.  Also, what's the exact model of your laptop? i'll try to find a how-to.

---

### Post by jackdelamare on 2008-03-28
Well I don't think I can do that on this laptop, so I'm going to uninstall Ubuntu and then there is an option on my "Rescue and Recovery" to restore but it gives me different options. One can be done from the latest backup made (I haven't done one) and another is something about applications, and the last is restoring to factory state, which I will probably end up doing. This would get Vista back for me and wouldn't destroy my product code, right?

---

### Post by lswest on 2008-03-28
well, restoring to factory settings wipes the hard drive, re-installs Vista, and adds all the software that was there before (it may or may not wipe the whole drive, or just the partition).  However, i swear that there is a way to get to a recovery console, did you try the F8 idea?

---

### Post by jackdelamare on 2008-03-28
F8 does nothing.

---

### Post by lswest on 2008-03-28
go to the link i posted above, download the ISO, burn it to a disk, boot to it, and run the commands from my first post.  Should fix it.  And remember, this is a linux forum, so help coming from here may or may not be on the mark.  However, the info i posted above should be good, unless the vista partition has been lost, or something else like that, though i do believe sda2 is the vista partition you want.

---

### Post by jackdelamare on 2008-03-28
Ok, I will try that, but I do have Rescue and Recovery on my Vista which loads by itself now, is this the same thing?

---

### Post by lswest on 2008-03-28
you said yourself there is no recovery console option in the Rescue and Recovery, so i assume the disk will give you the console you seem to be lacking.

> The Windows Vista DVD has a "recovery center" that provides you with the option of recovering your system via automated recovery (searches for problems and attempts to fix them automatically), rolling-back to a system restore point, recovering a full PC backup, or **accessing a command-line recovery console for advanced recovery purposes.**

what is in bold is what you need to be able to run the commands i posted.

---

### Post by stchman on 2008-03-28
> **jackdelamare said:**
> I am angry now, I did defragment and everything looked clean. So I've lost my Windows Vista? How great.
I used an OEM version of Windows Vista on my desktop PC, so, to save myself buying another one, should I use that CD in my laptop and use the product key on the bottom of my laptop? Would that work?
I also had some Lenovo software on there which allow the fingerprint login and webcam to work, so I'd loose all that?
Wow, Ubuntu just screws up my computer.

I triple boot XP, Vista,and Ubuntu.  They all coexist with each other very easily.  Ubuntu did not screw your PC up you did.  Think of it as a learning experience.  Remember Thomas Edison failed at making a light bulb about 10,000 times.  When asked he said that he found 10,000 ways that did not work.

Yes, use your OEM DVD to install Vista and use the key that came on the bottom of your laptop.

That proprietary software I am sure is on Lenovo's website.

---

### Post by jackdelamare on 2008-03-28
How the hell do I uninstall Ubuntu?!

---

### Post by lswest on 2008-03-28
> How the hell do I uninstall Ubuntu?! first off, no need for the language.  I can understand you're frustrated, but everyone here has other things to do in their life too, so be patient, and there are other posts on the forum of how to uninstall ubuntu, if you would search, you needn't have had to wait for a reply.  And secondly, to uninstall Ubuntu just delete the partition you installed it on.

---

### Post by jackdelamare on 2008-03-31
Sorry. I have now taken it out and Grub doesn't want to load, which is right as I took Ubuntu out, right? I'll definately need that CD that you gave me the link too though, as I cannot load Rescue and Recovery now.

---

### Post by jackdelamare on 2008-03-31
Thanks to lswest, the Vista Recovery CD worked and after looking around a bit I managed to restore my Windows Vista and it is now running smoothly. Unfortunately I do not have Ubuntu but who knows, one day I might.
Thanks for all the help everybody, I'm sorry for causing any trouble.

---

### Post by lswest on 2008-03-31
No problem, glad we got it sorted ^^ Would be nice if you came back for the release of 8.04, maybe try a WUBI install?  Anyways, always happy to have you.  And maybe you could mark this thread as solved (using the thread tools at the top of the thread) so that others know that a solution lies here?  Thanks!

---

