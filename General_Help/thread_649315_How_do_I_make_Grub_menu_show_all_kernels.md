---
title: "How do I make Grub menu show all kernels?"
date: 2007-12-24
forum: General Help
---

### Post by randell6564 on 2007-12-24
Hello!
I just installed the latest kernel for my Ubuntu 7.10.  Now my system randomly freezes, and  I have to do a hard-restart.  I only get the newest kernel option on my grub menu.  I want to use the previous kernel. I did a ```
sudo gedit /boot/grub/menu.lst
```and saw this already in there> ## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=allSo now I'm confused!  I have updated the kernel twice as I recall, but only one shows up on my boot menu.  Any Ideas?
Thanks!

---

### Post by Rocket2DMn on 2007-12-24
Can youi please post the contents of your menu.lst file?
If the old kernels are still listed there, they may need to be uncommented (have the # removed) or you might just need to uncomment one of those "howmany" lines.

---

### Post by adam.tropics on 2007-12-24
Not sure if I understand the whys and wherefores correctly on this, but I believe that since the last upgrade was minor/incremental (or whatever!) it would not show as a different kernel. It was 2.6.22-14.46 to 2.6.22-14.47. You could however select the previous one by forcing the version through synaptic I think. Someone correct me if I am wrong please.

---

### Post by randell6564 on 2007-12-24
> **Rocket2DMn said:**
> Can youi please post the contents of your menu.lst file?
If the old kernels are still listed there, they may need to be uncommented (have the # removed) or you might just need to uncomment one of those "howmany" lines.WOW, that was a quick reply! So, ok, you asked for it.  I only posted what I thought was the relevent part of my menu.lst ,but here it is in all it's glory!> # menu.lst - See: grub(8), info grub, update-grub(8)
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
default		4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		15

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
# kopt=root=UUID=53d6b3aa-9204-442e-a4c4-ef9dd6ad2984 ro

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
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=53d6b3aa-9204-442e-a4c4-ef9dd6ad2984 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=53d6b3aa-9204-442e-a4c4-ef9dd6ad2984 ro single
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
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1Thanks!

---

### Post by Rocket2DMn on 2007-12-24
OK, so GRUB doesn't list any other kernels - that either means you don't have them anymore or they just aren't in the file.  We can find out, please post the output of:
```
ls /boot/initrd.img*
ls /boot/vmlinuz*
```
This will list kernels you have available.

---

### Post by randell6564 on 2007-12-24
> **Rocket2DMn said:**
> OK, so GRUB doesn't list any other kernels - that either means you don't have them anymore or they just aren't in the file.  We can find out, please post the output of:
```
ls /boot/initrd.img*
ls /boot/vmlinuz*
```
This will list kernels you have available.This is weird.  Why are my old kernels not still hanging around?  output:> bigboss@bigboss-desktop:~$ ls /boot/initrd.img*
/boot/initrd.img-2.6.22-14-generic  /boot/initrd.img-2.6.22-14-generic.bak
bigboss@bigboss-desktop:~$ ls /boot/vmlinuz*
/boot/vmlinuz-2.6.22-14-generic
bigboss@bigboss-desktop:~$ 
Thanks!

---

### Post by nick_h on 2007-12-24
> **adam.tropics said:**
> I believe that since the last upgrade was minor/incremental (or whatever!) it would not show as a different kernel. It was 2.6.22-14.46 to 2.6.22-14.47.

Correct I only have one kernel for Gutsy.  The updates were minor.

---

### Post by adam.tropics on 2007-12-24
Would he be able to force version then? I can't see why not, although it would I imagine mean forcing version for other stuff too such as restricted modules and such.

---

### Post by Rocket2DMn on 2007-12-24
You don't have your old kernels anymore, I don't know what you did to upgrade, so I have no idea where they went, but you're out of luck for reverting to an older kernel with this method.  You should be able to download and install an older kernel, but I don't know how to go about this.  You can search around and check out google.  I still have my 2.6.22-9-generic kernel (I think it's from Feisty), but I've never booted to it since I upgraded.  You might be able to get that from a LiveCD of Feisty, but I'm not sure of the correct method to go about that.

EDIT: You can search on google for kernels available from the repositories, for example: [http://packages.ubuntu.com/feisty/base/linux-image-generic](http://packages.ubuntu.com/feisty/base/linux-image-generic)
under google search for ```
site:packages.ubuntu.com linux-image
``` and maybe include a version if you know what you had before.

Also search these forums for downgrading the kernel for gutsy.

---

### Post by nick_h on 2007-12-24
> Would he be able to force version then?

As you suggested earlier he could go into Synaptic and highlight the kernel image and then select Package->Force Version.  When you do this there is an option to downgrade to version 46.  However there is also the following warning: "If you force a different version from the default one, errors in the dependency handling can occur."

---

### Post by randell6564 on 2007-12-24
> **Rocket2DMn said:**
> You don't have your old kernels anymore, I don't know what you did to upgrade, so I have no idea where they went, I didn't do anything but click on the 'Update Notifier' icon.  I have never done any kind of system modifications.  Oh well..,I can live with this for now.  Doesn't seem to be freezing at the moment.  Thanks for all your help 'Rocket2DMn'.  And everyone else as well!:popcorn:

---

### Post by nick_h on 2007-12-24
> I didn't do anything but click on the 'Update Notifier' icon.
That's all you need to do.  For the very minor updates the kernel is replaced.  You will only get an additional one when a 2.6.22-15 version is available.

---

### Post by Rocket2DMn on 2007-12-24
> **randell6564 said:**
> I didn't do anything but click on the 'Update Notifier' icon.  I have never done any kind of system modifications.  Oh well..,I can live with this for now.  Doesn't seem to be freezing at the moment.  Thanks for all your help 'Rocket2DMn'.  And everyone else as well!:popcorn:

Ah, yeah I thought you upgraded to a completely new version of the kernel.  You can check your logs to see what got upgraded and maybe try and narrow the parameters to pinpoint the problem.  Check for the entry in /var/log/apt/term.log to see what was upgraded.  If you think you know the cause, you might be able to downgrade that particular package.

---

### Post by randell6564 on 2007-12-24
> **nick_h said:**
> That's all you need to do.  For the very minor updates the kernel is replaced.  You will only get an additional one when a 2.6.22-15 version is available.Cool!  So.,if the "very minor" update causes my system to freeze, how do I go about reversing the update?
Thanks!

---

### Post by nick_h on 2007-12-25
> how do I go about reversing the update?

Run System->Administration->Synaptic Package Manager
On the left-hand-side select Status and Installed.
Scroll down to the packages starting "linux-" (or do a search for these)
In turn highlight each of the following:

linux-headers-2.6.22-14
linux-headers-2.6.22-14-generic
linux-image-2.6.22-14-generic
linux-libc-dev

From the menu select "Package->Force Version..."

The selection box gives you a choice of 46 or 47. Select 46 and click on "Force Version".

As I mentioned in a previous post you should use this with caution, but you can always revert back if necessary.  You also will not receive future updates for these packages until you remove the version forcing.

---

### Post by Hairy_Palms on 2007-12-25
Just a small note, a power cycle isnt the best way to recover from a hard lock, press alt+sysrq and type REISUB to shutdown more cleanly.

---

