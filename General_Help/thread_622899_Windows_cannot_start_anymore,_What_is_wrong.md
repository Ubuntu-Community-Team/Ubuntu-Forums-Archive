---
title: "Windows cannot start anymore, What is wrong?"
date: 2007-11-25
forum: General Help
---

### Post by Stainless Steel on 2007-11-25
When i pick from the OS list it just stays on 

starting up...
_


What is wrong? Anything i need to do? Reinstall windows?

---

### Post by 1337455 10534 on 2007-11-25
Can you still boot into Ubuntu (if so which version do you use?). If not, than something very bad is happening. :).

---

### Post by Stainless Steel on 2007-11-25
Yeah I'm in Ubuntu right now.

I just got it from the download page yesterday.

---

### Post by cotcot on 2007-11-25
I guess that windows was not closed properly. You will not be able to mount the windows partition without forcing it either.
I had the same observation.
I decided to reinstall windows. So booting from the XP install CD. I indicated NOT to reformat the XP partition. The CD checked the partition and asked for a reboot just after checking the partition. I did a reboot but REMOVED the install CD. Windows was again ok. I do not know what happened but I could only be happy that the windows was repaired. PLEASE BE CAREFUL.

---

### Post by AgentZ86 on 2007-11-25
> **Stainless Steel said:**
> Yeah I'm in Ubuntu right now.

I just got it from the download page yesterday.

Are you in Ubuntu from the hardrive or from the live CD ??

---

### Post by AgentZ86 on 2007-11-25
> **Stainless Steel said:**
> When i pick from the OS list it just stays on 

starting up...
_


What is wrong? Anything i need to do? Reinstall windows?

After you select Windows from the list, see if you can instantly hit F8 and try booting to savemode, it does sound like a improper shutdown problem.

then perhaps just shutdown in savemode and try to startup normally again and see what happens.

---

### Post by Stainless Steel on 2007-11-25
> **AgentZ86 said:**
> Are you in Ubuntu from the hardrive or from the live CD ??
I'm in Ubuntu from the Hard drive, Let me try the F8 thing. wish me luck.

---

### Post by AgentZ86 on 2007-11-25
> **Stainless Steel said:**
> I'm in Ubuntu from the Hard drive, Let me try the F8 thing. wish me luck.

Sometimes you have to hit F8 a several times while the initial windows process starts. 

Hopefully you can get to the windows boot screen which will have a list like:
boot normally
boot to safemode command prompt
boot to safemode with network support etc etc.
stuff like that

I would select safemode of some type, and try to get into your windows systems that way to diagnose etc.

If you get into safemode at least you know the system is still there. 
Post back your findings.

---

### Post by qqzhenyi on 2007-11-25
Can you post the content of your boot/grub/menu.lst file?
Which partition your Windows system is installed on?

---

### Post by Stainless Steel on 2007-11-25
> **qqzhenyi said:**
> Can you post the content of your boot/grub/menu.lst file?
Which partition your Windows system is installed on?

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
# kopt=root=UUID=f26cfd0e-f1f4-4bef-8253-32545c75d78f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f26cfd0e-f1f4-4bef-8253-32545c75d78f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f26cfd0e-f1f4-4bef-8253-32545c75d78f ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


I do not know the name of the partition.

---

### Post by Stainless Steel on 2007-11-25
I did the F8 thing. nothing happens.

All i see is: 

Starting Up...

I have a windows CD inside of the computer but when i restart it no Windows installation thing comes up.

---

### Post by #Reistlehr- on 2007-11-25
Can yuo reply the output of this command in terminal:

If you have a SATA drive:
```

sudo fdisk -l /dev/sda

```

If you have an IDE drive:
```

sudo fdisk -l /dev/hda

```

This code will list the partitions on the specified drive. This will help to confirm the contingency of the grub values in menu.lst to the respective drives.

---

### Post by Stainless Steel on 2007-11-25
> **#Reistlehr- said:**
> Can yuo reply the output of this command in terminal:

If you have a SATA drive:
```

sudo fdisk -l /dev/sda

```

If you have an IDE drive:
```

sudo fdisk -l /dev/hda

```

This code will list the partitions on the specified drive. This will help to confirm the contingency of the grub values in menu.lst to the respective drives.

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02cc02cb

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6581    52861851    7  HPFS/NTFS
/dev/hda2            6582       14405    62846280   83  Linux
/dev/hda3           14406       14593     1510110    5  Extended
/dev/hda5           14406       14593     1510078+  82  Linux swap / Solaris

---

### Post by AgentZ86 on 2007-11-25
When and how did this occur ?

Was it on initial installation or did it work fine and just started happening ??

Please advise

---

### Post by Stainless Steel on 2007-11-25
> **AgentZ86 said:**
> When and how did this occur ?

Was it on initial installation or did it work fine and just started happening ??

Please advise

I used a live disc, then installed.

I updated Ubuntu and turned the computer off for the night.
Next morning i wanted to play some games so i decided to boot into windows and notice the boot menu is different i choose windows 98/2000/xp (something like that) and the thing stays on starting up...

When i put my Windows CD in so i can reinstall windows the computer just goes back into the grub menu thing.

---

### Post by AgentZ86 on 2007-11-25
> **Stainless Steel said:**
> I used a live disc, then installed.

I updated Ubuntu and turned the computer off for the night.
Next morning i wanted to play some games so i decided to boot into windows and notice the boot menu is different i choose windows 98/2000/xp (something like that) and the thing stays on starting up...

When i put my Windows CD in so i can reinstall windows the computer just goes back into the grub menu thing.

Depending on your system you may have to hit F12 to get a sort of mini bios menu that allows you to select to boot from the CD. if the bios is not letting you boot to the CD currently. This is typical with Dell and IBM Systems as well as many others.

Sometime even if you set the CD in the bios as the first boot device it will still boot to the hardrive unless you hit F12 to boot to CD.

As far as reinstalling windows I don't know how this effect the linux partition or grub, but I recall doing this on my system and there was no problem that I can remember

I'm not sure how to fix grub if you install windows over the active boot partition.

Anyhow thats all I know, let me know how the F12 pans out.

Once you get it to boot to the windows CD you can repair the xp parition.

Example to repair Master boot record of your XP installation:

Boot with the XP installation CD.

When prompted, press R to repair a Windows XP installation.

If repairing a host with multiple operating systems, select the appropriate one (XP) from the menu. If you have only one operating system, enter 1 to select it.

Enter the administrator password if prompted.

To fix the MBR, use the following command:

fixmbr


This assumes that your installation is on the C:\ drive. You will be presented with several scary warning lines the reading of which will make you want to say no. Microsoft is exceptionally vague regarding the conditions under which fixmbr can cause problems although they are clear about the consequences (losing all data on the hard drive), so use this at your own risk.

Type y and ENTER to fix the MBR.

Type exit to leave the recovery console and reboot.

Anyhow that should do it. if you can get into your CD that is.

Hope this helps

---

### Post by hikaricore on 2007-11-25
Reinstalling ***dows will remove grub for sure.

There are several threads around here about fixing grub for ***dows booting, and reinstalling it after a reinstallation of ***dows.

---

