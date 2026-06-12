---
title: "Disable or edit grub to get rid of OS menu at bootup"
date: 2007-05-22
forum: General Help
---

### Post by justinae on 2007-05-22
I'm pretty new but understand a little. Due to a partition that Feisty used to be installed on I am getting a menu choice during bootup that asks me which OS I want to load. I only have one partition with the OS on it so do I edit Grub or somehow disable it. Is grub only relavent if I have more than 1 OS or is it standard no matter what?

BTW, the active partition that I have is hda3

Here is my menu.lst:

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
# kopt=root=UUID=8ead7354-98ef-4ea4-84d4-6d44e5a2dbda ro

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
# howmany=1

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8ead7354-98ef-4ea4-84d4-6d44e5a2dbda ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8ead7354-98ef-4ea4-84d4-6d44e5a2dbda ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.20-15-generic (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=1fcf21d0-344b-4d73-ae56-9bafad15efed ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=1fcf21d0-344b-4d73-ae56-9bafad15efed ro single 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, memtest86+ (on /dev/hda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot
```

---

### Post by seamuso on 2007-05-22
> **justinae said:**
> I'm pretty new but understand a little. Due to a partition that Feisty used to be installed on I am getting a menu choice during bootup that asks me which OS I want to load. I only have one partition with the OS on it so do I edit Grub or somehow disable it. Is grub only relavent if I have more than 1 OS or is it standard no matter what?

BTW, the active partition that I have is hda3

Here is my menu.lst:

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
# kopt=root=UUID=8ead7354-98ef-4ea4-84d4-6d44e5a2dbda ro

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
# howmany=1

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8ead7354-98ef-4ea4-84d4-6d44e5a2dbda ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8ead7354-98ef-4ea4-84d4-6d44e5a2dbda ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.20-15-generic (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=1fcf21d0-344b-4d73-ae56-9bafad15efed ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=1fcf21d0-344b-4d73-ae56-9bafad15efed ro single 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, memtest86+ (on /dev/hda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot
```

uncomment hiddenmenu

make sure that the default what you want to boot ..


default		0  

boots this - 

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8ead7354-98ef-4ea4-84d4-6d44e5a2dbda ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

and depending on how long you want to give it to start the boot, change the timeout to something smaller (I have mine set to 3)

---

### Post by justinae on 2007-05-22
hey thanx seamuso. i'll try that. is that a "workaround" or is that what the menu.lst file would look lik on a fresh install as well?

---

### Post by seamuso on 2007-05-22
> **justinae said:**
> hey thanx seamuso. i'll try that. is that a "workaround" or is that what the menu.lst file would look lik on a fresh install as well?

It isn't really a workaround, it's the basic option set in grub .. 

[http://www.gnu.org/software/grub/manual/html_node/Commands.html#Commands](http://www.gnu.org/software/grub/manual/html_node/Commands.html#Commands) 

there's a list of all the commands

I think it's picking up the other install. Whne I installed feisty beta, the boot menu was hidden. When I did my release install of feisty (kubuntu) it started kicking the menu up at me.

When I had installed the beta, I had isolated my pata drives off from my sata that had my LFS and XP installs, so I don't know what it would have done had those disks been active/available.

---

### Post by justinae on 2007-05-22
it worked. i've got it set to 1 second and it goes smooth. thanx for all the help.

---

### Post by fragos on 2007-05-22
True you have one partition but all three choices given are images within that partition.  The recovery image is important if you need to perform a recovery because some change you've made to configuration files prevents the GUI from booting up.  Recovery mode is basically command line without GUI.  The default timeout to have grub decide which to boot is 10 seconds.  By default, it will select the first entry which is full Ubuntu with GUI.

---

### Post by justinae on 2007-05-22
thanx fragos. the problem is that there is a recovery version of my current install, and a recovery of an old install. where is the recovery stored so i can remove it and only have current versions?

---

### Post by fragos on 2007-05-22
The recovery image isn't realy a separate image.  Grub parameters are used to get it to boot as GUI or recovery.  See the following from my system:

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=bed0f6dd-b550-4d2c-93cb-cf9c42656831 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=bed0f6dd-b550-4d2c-93cb-cf9c42656831 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

---

### Post by justinae on 2007-05-22
that makes sense. but i have two separate versions of both the regular and recovery mode. see the following:

these are my regular ones

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8ead7354-98ef-4ea4-84d4-6d44e5a2dbda ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8ead7354-98ef-4ea4-84d4-6d44e5a2dbda ro single
initrd		/boot/initrd.img-2.6.20-15-generic


these are the ones from an old install and the partition doesn't even exist anymore

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.20-15-generic (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=1fcf21d0-344b-4d73-ae56-9bafad15efed ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=1fcf21d0-344b-4d73-ae56-9bafad15efed ro single 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot

---

### Post by seamuso on 2007-05-22
If you have entries that no longer pertain to anything, you can remove them. You just have to make sure that the default is set correctly (and making a copy of your menu.lst for safekeeping never hurts either).

All that grub really cares about is whether or not it knows what partition to boot. when I have an LFS system running, it's not uncommon for me to have several different kernel builds in my /boot plus entries for those plus entries for any other linux installs that are available on my system.

BTW, solaris installs and uses grub also .. pretty much same scenario as ubuntu .. full kernel and a safe boot kernel .. :p

---

### Post by justinae on 2007-05-22
gotcha. hey thanx again for the help! I've learned more about linux/ubuntu in the last week than I ever thought I would know and it's cause of people like you (and a wee bit of google too. ) :)

---

### Post by fragos on 2007-05-23
The parameters I was talking about are "ro quiet Splash" vs "ro single".  If you're an Ubuntu user, run synaptic and search for "linux-image-2.6.20".  you'll see "-15-generic" marked as installed.  There might be other versions like -13 or whatever.  If the older versions are marked as installed you can tell synaptic to remove them.  Grub will be automaticaly updated to reflect that they are gone.  I regularly remove old versions of the kernel that way and never have to manualy edit menu.lst to change grub.  With Ubuntu 7.04 grub handling has much improved and wwhen grub is rebuilt even OS versions in other partitions are found and added to menu.lst.

---

