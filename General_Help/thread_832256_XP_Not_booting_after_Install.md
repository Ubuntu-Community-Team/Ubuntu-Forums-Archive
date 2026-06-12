---
title: "XP Not booting after Install"
date: 2008-06-17
forum: General Help
---

### Post by MrKMrK on 2008-06-17
Hey, I just installed ubuntu this morning and played around in it for a few hours, and am now trying to get back into XP Home. The grub menu loads up on boot, I scroll to XP Home, and then it just says "Starting Up..." in the top left of the screen. I tried to find a solution on the forums and on the interwebs, but no dice. So, here is the stuff you're probably going to ask for:

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify		(hd0,0)
savedefault
makeactive
chainloader	+1 
```

Windows is definitely in the "sda1" area. 

I've really got no idea. I've never used linux before, so I'm completely at a loss. Reformatting isn't really an option I'd like to consider =/.

---

### Post by Captain_Riker on 2008-06-17
Hello,

can you be a little more specific? Is it a Win XP "Starting up"?

Can you place a complete copy of your menu.lst?

Which steps have been performed at install, i.e. related to formatting partitions, create new ones. Adding mountpoints for the linux System and hints that Ubuntu found other os's?

Or simply how's your partition table? You might have accidently installed Ubuntu over your XP and grub just found the MBR entries and "suggested" that XP is still there . . .

---

### Post by MrKMrK on 2008-06-17
> **Captain_Riker said:**
> Hello,

can you be a little more specific? Is it a Win XP "Starting up"?

Can you place a complete copy of your menu.lst?

Which steps have been performed at install, i.e. related to formatting partitions, create new ones. Adding mountpoints for the linux System and hints that Ubuntu found other os's?

Or simply how's your partition table? You might have accidently installed Ubuntu over your XP and grub just found the MBR entries and "suggested" that XP is still there . . .

The "Starting Up..." was just white text on black background, DOS style. 

When I chose how I was partitioning, I chose to give 30gb to ubuntu, and I had 70 available that windows wasn't using (the HDD is 320gb). I'm not sure of the option, but I know there was a slider involved =/.

Here is my fdisk -l

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x21e6d7c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       26199   210443436    7  HPFS/NTFS
/dev/sda2           26200       30401    33752565    5  Extended
/dev/sda5           26200       30222    32314716   83  Linux
/dev/sda6           30223       3
```

I think I've really messed some stuff up now. I read on another page to try using the recovery disk, and in recovery mode, type fixmbr and fixboot. Since then, I haven't been able to even boot Linux without the use of a supergrub disc and otherwise it just says "Disc read error: hit Ctrl+alt+delete to restart."

I tried reinstalling windows over my old installation (all old files are kept, just windows gets a reinstall) and that appeared to have accomplished nothing. 

Anyways, here is the big menu.lst

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
# kopt=root=UUID=dbbb9d08-1f78-4d55-a2e5-df369eb89924 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=dbbb9d08-1f78-4d55-a2e5-df369eb89924 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=dbbb9d08-1f78-4d55-a2e5-df369eb89924 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by Captain_Riker on 2008-06-18
There are a couple of things strange about your partition layout.
A porper layout would look like this:

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          16      128488+  83  Linux
/dev/sda2              17        1036     8193150   82  Linux swap
/dev/sda3            1037        1673     5116702+  83  Linux
/dev/sda4            1674       19452   142809817+   5  Extended
/dev/sda5            1674       19452   142809786   83  Linux

```

You lack the swap partition? Or is it the last line of your pasting that's not complete?

> 
/dev/sda6           30223       3


Anyways, by running FIXMBR you messed up the Startup entries in your Master Boot Record for Linux, that's why it is "gone". As you might assume it is still there but all info on booting is missing.

You tried reinstalling Windows to no avail? Hmm, that's weired. The usual way of getting a Dual Boot System is to install Windows first and then Linux. So If you "started" fresh, so to say every thing, Windows related should start to work properly again. So after the reinstall you still get "Disc read error: hit Ctrl+alt+delete to restart."?

If so the easiest way would be to  . . . reformat.
You can either boot from your Ubuntu install Disc. After the System has booted try and mount the ntfs partition and then plug in an external drive. After that you can browse your ntfs partition and copy your files /data to the external drive (you might as well need a tool like ntfs-3g to fully accomplish writing the files to the external drive). Or, if you have another windows machine at hand use BartPEBuilder ([http://www.nu2.nu/pebuilder/#download](http://www.nu2.nu/pebuilder/#download)) to create a Windows LiveCD. Thus you can be sure you'll be able to move your Data.

After saving your Data you'd create a Proper Partition Layout with Partition Magic or (in my opinion even better) the gparted LiveCD. Repartitioning should fix your troubled mbr. Choose a partition for

* Windows as NTFS (25 to 30 GB are way enough, unless you play a lot of games),

this time also choose to create

*a partition for your Data, format it as FAT32(vfat) 

this way Linux and Windows will be able to access(read and write) the partition. There should also be a 250MB sized 

*partition in ext3 to be labled /boot. 

*Then a partition for your Linux ("/")and, most important the 

* Swap partition.

After formatting your drive, install Windows XP on the ntfs partition. Then install Ubuntu, assigning the appropriate Partitions to the lable's (/boot, /) and set the mount point for you vfat drive. This way it will automatically be added to your fstab and you don't need to do this manually after the install.

If Both Systems will boot cleanly after finishing then, well, go ahead, copy back your data to the fat32 partition, install all the necessary programms in Windows (aah, update it first ;-)) and so on.

Sorry to offer no other help then this, but it seems that there is something wrong with the "layout" of your mbr. You can as well try and launch the windows XP install CD (or another recovery CD) and try to fix your your MBR once more. I have been reinstalling my XP once or twice as well by messing something up. I used a Win98 Recovery Floppy and executed fixmbr. Maybe omit fixboot this time.

But I recommend the fresh "wipe and start again". Cause there are multiple issues possible. Another thing could be a corrupted boot.ini for windows. Or something. Sorry . . .

---

