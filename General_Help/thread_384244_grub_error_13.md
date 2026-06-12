---
title: "grub error 13"
date: 2007-03-14
forum: General Help
---

### Post by hellfried on 2007-03-14
i just installed kubuntu edgy eft on the 3rd partition on my hd. i have winxp and ubuntu edgy on the other 2. i decided that i wanted my old ubuntu grub menu and restored it using the ubuntu live cd. 
i added kubuntu as one of the options in the menu but when i select it i get an 'error 13 : invalid or unsupported executable format'. how do i boot into kubuntu. this is what my /boot/grub/menu.lst looks like - 

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
default		6

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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
# kopt=root=UUID=5a699f92-9a66-4174-ac01-bc5f404b3c76 ro
# kopt_2_6=root=/dev/sda2 ro

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

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

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

title           Kubuntu
root            (hd0,2)
chainloader     +1

i am quite sure that the entry for kubuntu is wrong, how should it look like?
I got this from my previous install of fedora on the same partition. thanks in advance.

---

### Post by markitect on 2007-03-14
Changing the root and using chainloader is really just for windows.  If you want to have an option to open up your kubuntu menu  you want something like

```

title Kubuntu
configfile (hd0,2)/boot/grub/menu.1st

```

if you do this  you should also add and entry in your kubuntu menu.lst that loads the menu.lst for ubuntu so you can switch back and forth easily

or just copy the entires from your kubuntu menu.1st to the ubuntu one.

---

### Post by hellfried on 2007-03-15
if i paste the entries in my kubuntu menu.lst to the ubuntu one i will end up with a very cluttered meun list. i guesss i can always put a # in front  of the entries that i do not want...

---

### Post by confused57 on 2007-03-15
> **hellfried said:**
> if i paste the entries in my kubuntu menu.lst to the ubuntu one i will end up with a very cluttered meun list. i guesss i can always put a # in front  of the entries that i do not want...

What you could do is use the live cd to install Kubuntu's grub to its root partition:
```
sudo grub
find /boot/grub/stage1
root (hd0,2)
setup (hd0,2)
quit
```

this should allow you to boot to Kubuntu with your current menu.lst entry

See this link for a more detailed explanation:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

---

### Post by _Paladin on 2007-04-23
I seem to be having a problem too with "Error 13"  here is what the grub super cd says when I try to boot it from there:


Booting 'Ubuntu, kernal 2.6.20-15-generic'

root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83
kernal /boot/vmlinuz-2.6.20-15-generic root=UUID=ebc4d9c9-1ad0-42aa-8563-85c5e
0e96635 ro quiet splash

Error 13: Invalid or unsupported executable format

Press any key to continue...

It is kubuntu 7.04 on a OmniBook XE3.  I have been having serious issue loading anything onto this machine, and Kubuntu was the first thing I was able to install.  After a successful installation of this Distro (After trying different things maybe 30 times with several distributions), the error 13 message was the only thing that came out.  

I'm still quiet a bit of a newb.  Thanks for any help

---

### Post by _Paladin on 2007-04-26
bump

---

