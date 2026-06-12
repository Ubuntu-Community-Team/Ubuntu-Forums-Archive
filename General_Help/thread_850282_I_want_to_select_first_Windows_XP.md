---
title: "I want to select first Windows XP"
date: 2008-07-05
forum: General Help
---

### Post by sowhat12345 on 2008-07-05
When I open my computer , I see a black screen where I can select which operation system I want to start . There are 4 options : Ubuntu 8 , 2 opitons for Ubuntu (recovery and something...) and Windows XP. I want Windows XP to be in the first option (line) . What should I do ?
(the black page is like that : [http://images.howtoforge.com/images/unetbootin_windows_linux/big/36.png](http://images.howtoforge.com/images/unetbootin_windows_linux/big/36.png) )

---

### Post by f37u5g0d on 2008-07-05
Get the start-up manager from the repos.  It's in add/remove if you prefer that.  After you download/install it will show up in your System > Administration menu.  The handy utility allows you to adjust many start-up options including the default operating system.  It won't change the order they are listed but it will make whichever one you choose the one that is highlighted on start-up.

---

### Post by VMC on 2008-07-05
> **sowhat12345 said:**
> When I open my computer , I see a black screen where I can select which operation system I want to start . There are 4 options : Ubuntu 8 , 2 opitons for Ubuntu (recovery and something...) and Windows XP. I want Windows XP to be in the first option (line) . What should I do ?
(the black page is like that : [http://images.howtoforge.com/images/unetbootin_windows_linux/big/36.png](http://images.howtoforge.com/images/unetbootin_windows_linux/big/36.png) )

You mean the first line or the default boot. There a bit different.
output Grub menu and we can explain:

From a Terminal type:
```
cat /boot/grub/menu.lst
```

---

### Post by sowhat12345 on 2008-07-05
VMC ; I mean the first line . I don't know which operation system is my default . I install Ubuntu seperate from the Windows XP , I mean I install it in the free space which is being not used by Windows XP .
f37u5g0d ; I can't install anything in the Ubuntu because I don't have internet connection .

[I][B]yusuf@yusuf-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=f8e4127d-1dce-4485-88cf-e16112c0641a ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f8e4127d-1dce-4485-88cf-e16112c0641a ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f8e4127d-1dce-4485-88cf-e16112c0641a ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
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

yusuf@yusuf-desktop:~$[/B][/I]

Is there a simple way to do that ?

---

