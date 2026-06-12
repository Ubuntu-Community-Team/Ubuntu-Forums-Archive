---
title: "GRUB problems - loading old Kernel"
date: 2008-04-26
forum: General Help
---

### Post by eludlow on 2008-04-26
When I upgraded from Gutsy to Heron, I chose to keep my old menu.lst file as I dual boot.  However, I've now realised this is making Ubuntu load the wrong kernel, so I want to reinstall GRUB, or more specifically, just have the "default" menu.lst file.

I've downloaded the 8.04 ISO and burned, and followed the guide at [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) but my GRUB loader is still the old version, hence still the old Kernel.

Anyone got any suggestions?  If someone posted their menu.lst file, would I just be able to use that, assuming of course I change the hard disk references to mirror my system.  I can then add the boot option for Windows later on.

Thanks,
Ed Ludlow

---

### Post by zvacet on 2008-04-26
In synaptic search box type **linux-image** and you will see all kernel you have installed.See if new one is listed.If you want to you can delete all exept that one.probably you have to many kernels installed and new one can not be listed in grub.

---

### Post by p_quarles on 2008-04-26
If you can post the output of these commands:
```
dpkg --get-selections linux-image-*
```
and
```
uname -a
```
I can tell you how to edit your /boot/grub/menu.lst to make it recognize and boot the new kernel.

---

### Post by eludlow on 2008-04-26
> dpkg --get-selections linux-image-*

> linux-image-2.6.22-14-generic                   install
linux-image-2.6.24-16-generic                   install
linux-image-generic                             install

> uname -a

> Linux ludlow 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux

And the contents of my current menu.lst is as follows:

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
timeout		30

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
# kopt=root=UUID=1e22154a-7e1b-4ff7-9b59-7765ea2b58ab ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=1e22154a-7e1b-4ff7-9b59-7765ea2b58ab ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=1e22154a-7e1b-4ff7-9b59-7765ea2b58ab ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title		Windows XP
root 		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST


(the only change I've made to that since upgrading to Hardy Herson is changing "Ubuntu 7.10" to "Ubuntu 8.04" :)

Many thanks!

---

### Post by p_quarles on 2008-04-26
Okay, you need to place the following two lines in your menu.lst file:
 ```

 title Ubuntu 8.04, kernel 2.6.24-16-generic
 root (hd0,0)
 kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=1e22154a-7e1b-4ff7-9b59-7765ea2b58ab ro quiet splash
 initrd /boot/initrd.img-2.6.24-16-generic
 quiet
 
 title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
 root (hd0,0)
 kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=1e22154a-7e1b-4ff7-9b59-7765ea2b58ab ro single
 initrd /boot/initrd.img-2.6.24-16-generic
```
These lines should right after the line that says "END DEFAULT OPTIONS" and right before the other Ubuntu boot stanzas.

---

### Post by eludlow on 2008-04-26
Brilliant, thank you!  That's all working fine :)

I take it there's not really any need to keep the old entries, which point at the older kernel?

Again, thank you.

---

### Post by p_quarles on 2008-04-26
> **eludlow said:**
> Brilliant, thank you!  That's all working fine :)

I take it there's not really any need to keep the old entries, which point at the older kernel?

Again, thank you.
Yeah, keep the old entries around until you're absolutely sure that the new kernel works okay for you under the whole range of circumstances.

---

### Post by jblackhall on 2008-04-26
(see below)

---

### Post by jblackhall on 2008-04-26
> **p_quarles said:**
> Okay, you need to place the following two lines in your menu.lst file:
 ```

 title Ubuntu 8.04, kernel 2.6.24-16-generic
 root (hd0,0)
 kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=1e22154a-7e1b-4ff7-9b59-7765ea2b58ab ro quiet splash
 initrd /boot/initrd.img-2.6.24-16-generic
 quiet
 
 title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
 root (hd0,0)
 kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=1e22154a-7e1b-4ff7-9b59-7765ea2b58ab ro single
 initrd /boot/initrd.img-2.6.24-16-generic
```
These lines should right after the line that says "END DEFAULT OPTIONS" and right before the other Ubuntu boot stanzas.

Isn't this a bad idea because the problem is that those 2 lines are not being added by update-grub.  Thus, whenever grub is updated (such as with a kernel upgrade) those lines will be deleted.  The real issue here is that update-grub is not displaying his hardy kernel, only the gutsy one.  The easiest way to remedy this (that I've found) is to uninstall the old linux kernel image (2.6.22-14).  This will allow update-grub to correctly load the kernels.  If there is a better way to do this though (without removing the old kernel), let me know.

See here:
[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/202009](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/202009)

---

### Post by p_quarles on 2008-04-26
> **jblackhall said:**
> Isn't this a bad idea because the problem is that those 2 lines are not being added by update-grub.  Thus, whenever grub is updated (such as with a kernel upgrade) those lines will be deleted.  The real issue here is that update-grub is not displaying his hardy kernel, only the gutsy one.  The easiest way to remedy this (that I've found) is to uninstall the old linux kernel image (2.6.22-14).  This will allow update-grub to correctly load the kernels.  If there is a better way to do this though (without removing the old kernel), let me know.

See here:
[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/202009](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/202009)
Yes, manually editing the menu.lst and letting it update automatically don't always mix well. The point here, though, is that the OP chose not to update them automatically with the version upgrade, as he was concerned about the dual-boot configuration.

---

### Post by eludlow on 2008-04-26
So if I install the old kernel (what's the simplest way of doing this btw?) when grub updates, I shouldn't need to edit menu.lst every time grub updates?

---

### Post by jblackhall on 2008-04-28
I still think you should realize that p_quarles's solution is only temporary for you.  I believe your problem is that you've still got the old (Gutsy, 2.6.22-14) kernel installed.  You should also have the Hardy kernel (2.6.24-16) installed.  You told the Upgrade program to "keep my menu.lst" as opposed to "install the package maintainer's version".  The problem is that after choosing that option, Ubuntu thinks you want to be using the Gutsy kernel permanently.

Right now you've manually edited menu.lst to load your correct kernel. The part you've edited is normally "automagically" filled in by the update-grub function using the options in menu.lst (all the lines with #'s) and the current kernel version you've told Ubuntu that you want to use. The thing is, whenever the update-grub function is run (like for future kernel upgrades in Hardy), it's going to overwrite any changes you made to the "automagic" list to reflect the kernel Ubuntu thinks you want to be using (the gutsy one).  To remedy this permanently, you really should uninstall the Gutsy kernel.  You will then be prompted with the same menu.lst question as when you upgraded.  You should tell it to use the package maintainer's version this time.  For me, it preserved the options for my Windows partition and also extra options I had put in there.  It only updated the kernel that update-grub uses when it runs.  If you're concerned about losing something important in your menu.lst then just make a back up copy first.

There really should be no reason for the Gutsy kernel to still be installed that I can see unless you have some specific problem with the newer Hardy one.  If you'd like to re-install it along side the current Hardy one, that should be possible.

---

### Post by Kuzja on 2008-04-29
I was having the same issues and after editing my menu.lst Ubuntu started to use the proper kernel. But as far as understand from jblackhall's post it can not be a permanent solution and I need to uninstall Gustsy kernel. The question for me now is how i do that.

---

### Post by eludlow on 2008-04-30
First backup menu.lst

Go to Synaptic package manager, and search for linux-image - then check anything referring to the old kernel - anything ending in -14 it will be.

Click "apply" I think it is and then it will remove, then the grub setup menu will appear again, so click the top option, for the menu.lst that comes with the distro, and it will wipe you current version.  The open your NEW menu.lst and make the chanes that you will be able to copy from your backup.

Ed

---

### Post by Kuzja on 2008-05-01
Thanks a lot. It worked flawlessy, except that it didn't give me any options and just created a new menu.lst. However, thanks to a back up copy I could preserve my past setup.

---

### Post by eludlow on 2008-05-01
Glad I could help! :)

---

