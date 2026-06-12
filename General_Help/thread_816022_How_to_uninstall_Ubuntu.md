---
title: "How to uninstall Ubuntu"
date: 2008-06-02
forum: General Help
---

### Post by gaffajoiner on 2008-06-02
I have Ubuntu installed on my laptop, with vista as well, had trouble with the update manager would only part update then it said could not update, so i put the Ubuntu disc in and installed it,but it has put 2 on so when i boot up it list a few so if i select the one i have just installed i cannot get on line so when i reboot and pick Vista it comes up with Vista/Ubuntu so i select Ubuntu and i an back to the first Ubuntu i installed, and can get on the internet,and update manager is now working, how do i uninstall the last one of Ubuntu so i only have one installed

---

### Post by housam on 2008-06-02
Just format the partition you installed the last ubuntu on it, 
reinstall grub because the last system you installed overwrote  the mbr.
You can edit the grub menu.lst to make the unwanted kernels from appearing in the grub menu by adding # in front of the lines of these kernels then save and reboot.

---

### Post by gaffajoiner on 2008-06-02
Thanks for the help, have installed grub, being a newbie where do i find the partition i installed it on

---

### Post by housam on 2008-06-02
restart your computer and when the grub menu pop-up move the arrow downward to stop the counter of the automatic start.
at each kernel line end , there is a note about the partition that has that kernel like ( hda2 ) or (sda3 ).
note the partition of the kernel you want to remove.and reformet it.

install grub after formatting the partition

---

### Post by gaffajoiner on 2008-06-02
Hi
Done as you said but they still show, i rebooted then when the menu came up, i pressed the down arrow on each one but there was no note at the end of any, it just highlighted each one, so i downloaded grub 2 number one is edit, put a hash at the beginning of each line, not the default one but 2 Ubuntu with recovery with closed brackets.

---

### Post by gaffajoiner on 2008-06-02
I put the hash at the end of the line but still shows, on mine there is no save button ,it has a apply and a OK button which i pressed on each

---

### Post by housam on 2008-06-02
To edit grub menu :
Go for application >> accessories >> terminal and type the following code :
```
 gksu gedit /boot/grub/menu.lst
```
you will see somthing like that 
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
color cyan/blue white/green

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=fde58ebd-aee0-485e-8e61-58b739d00877 ro

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
[COLOR="Red"]
#title		Ubuntu 8.04, kernel 2.6.24-17-386
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.24-17-386 root=UUID=fde58ebd-aee0-485e-8e61-58b739d00877 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-17-386
#quiet

#title		Ubuntu 8.04, kernel 2.6.24-17-386 (recovery mode)
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.24-17-386 root=UUID=fde58ebd-aee0-485e-8e61-58b739d00877 ro single
#initrd		/boot/initrd.img-2.6.24-17-386[/COLOR]

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=fde58ebd-aee0-485e-8e61-58b739d00877 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=fde58ebd-aee0-485e-8e61-58b739d00877 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fde58ebd-aee0-485e-8e61-58b739d00877 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fde58ebd-aee0-485e-8e61-58b739d00877 ro single
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
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda9.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/sda9)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d677c812-2a04-48de-ba9d-840aba29b9ec ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda9.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda9)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d677c812-2a04-48de-ba9d-840aba29b9ec ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda9.
title		Ubuntu 8.04, memtest86+ (on /dev/sda9)
root		(hd0,8)
kernel		/boot/memtest86+.bin  
savedefault
boot


THIS is mine and you can see that I marked the unwanted kernel with the hash ( lines in red ) , then save the file and reboot.

---

