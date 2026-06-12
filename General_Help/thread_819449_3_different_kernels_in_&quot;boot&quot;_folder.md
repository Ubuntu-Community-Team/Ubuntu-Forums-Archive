---
title: "3 different kernels in &quot;boot&quot; folder"
date: 2008-06-05
forum: General Help
---

### Post by linuxguy6 on 2008-06-05
After running Update Manager, the updater shows I need kernel updates. I hit OK, and it all seems to be going along OK. Thinking everything was OK, I rebooted my system and see that disk usage is way up. I check the "boot" folder and find three different versions of everything. I open a terminal and check the installed kernel version using uname -u, and it shows 2.6.24-16-generic. Also in the folder is 2.6.24-17-generic and 2.6.24-18-generic. I also understand there is a 2.6.25.4 kernel available (I have downloaded it). Why doesn't the kernel update itself, and how can I install 2.6.25.4? :confused:

---

### Post by bingoUV on 2008-06-05
Where did you download 2.6.25.4 from? In what form? deb? source? Post the filename here if you are not sure.

Did you reboot after updating? If yes, post the file /boot/grub/menu.lst here. For some reason, the newer kernels did not boot by default.

If you did not reboot after updating, you need to do that for kernel update to take effect.

---

### Post by pointone on 2008-06-05
[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

[https://wiki.ubuntu.com/KernelUpdates](https://wiki.ubuntu.com/KernelUpdates)

---

### Post by linuxguy6 on 2008-06-05
bingoUV:
I downloaded the 2.6.25.4 kernel from [www.kernel.org](www.kernel.org) in a bzip2 format. The filename is patch-2.6.25.4.bz2
I did reboot after updating to 2.6.24.18
Here are the contents of my menu.lst:
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
# kopt=root=UUID=9c624de4-a8fb-4c12-9723-3cb8f8809aa4 ro

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

title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9c624de4-a8fb-4c12-9723-3cb8f8809aa4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9c624de4-a8fb-4c12-9723-3cb8f8809aa4 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

I manually edited it.:)

---

### Post by bingoUV on 2008-06-05
I see the default looks like windows. There is no mention of the .18 kernel. Maybe because you edited it manually, the kernel deb might not have been able to add the entry for newer kernels. Add the entries for newer kernels.

To install new kernel, you will have to compile it. Since it seems to be a patch on a previous version (don't know which one) you will have to create the source using the previous version and this patch. Then, read [http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html](http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html) for a guide to compile kernel. I have not tried it, there may be better guides available.

---

### Post by bingoUV on 2008-06-05
I see the default looks like windows. There is no mention of the .18 kernel. Maybe because you edited it manually, the kernel deb might not have been able to add the entry for newer kernels. Add the entries for newer kernels.

To install new kernel, you will have to compile it. Since it seems to be a patch on a previous version (don't know which one) you will have to create the source using the previous version and this patch. Then, read [http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html](http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html) for a guide to compile kernel. I have not tried it, there may be better guides available.

---

### Post by geirha on 2008-06-05
Next time there's a kernel-upgrade, your windows-entry will be gone in that menu.lst. Read about the automagic kernels list at [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto) to see why.

---

### Post by linuxguy6 on 2008-06-06
I have solved part of my problem. I manually edited the menu.lst file to get the 2.6.24-18-generic kernel to boot. I am looking into compiling the 2.6.25-24-generic kernel.:)

---

### Post by bingoUV on 2008-06-06
It might be a lot quicker to use kernel from this RPM [ftp://archive.linux.duke.edu/pub/fedora/linux/updates/9/i386/kernel-2.6.25.3-18.fc9.i686.rpm](ftp://archive.linux.duke.edu/pub/fedora/linux/updates/9/i386/kernel-2.6.25.3-18.fc9.i686.rpm) . Extract using rpm2cpio (maybe in repositories, otherwise google it). Place vmlinuz and initrd in /boot; modules in their appropriate place; make grub entries and it might even work. Worth a try in my opinion.

---

### Post by lswb on 2008-06-06
A kernal update susing synaptic usually will reconfigure your grub boot menu to add the new kernal as the default boot option, but that seems to not have happened for some reason in your case. Make a backup of your menu.lst file in /boot/grub, and run

---

