---
title: "GRUB-StartupManager : wrong kernel"
date: 2008-05-04
forum: General Help
---

### Post by sgissinger on 2008-05-04
Hi all.
I upgraded to Hardy Heron. 
GRUB now shows me 3 different ubuntu 8.04 kernels.
This is why I installed Startup-Manager and set the max different kernels to 1.
As a result, at next reboot, the only kernel left is :
"Ubuntu 8.04, kernel 2.6.24-16-server" (+recovery mode)
This kernel doesn't work with my CPU (I assume this is normal since the kernel is designed for server CPUs) and I'd like to get my other kernels back and, if possible, delete this damn server kernel from my GRUB menu.
Thanks

---

### Post by macaholic on 2008-05-04
Does the recovery kernel boot at all? If it even allows you to drop to a command line you can edit your /boot/grub/menu.lst file to include more kernels.

---

### Post by sgissinger on 2008-05-04
No when I select the server kernel's recovery mode, I get the same error message (CPU not supported or something).
please help me!

---

### Post by TeoBigusGeekus on 2008-05-04
Boot up with a live cd and post us the content of your /boot/grub/menu.lst file (.LST)

---

### Post by macaholic on 2008-05-04
> **TeoBigusGeekus said:**
> Boot up with a live cd and post us the content of your /boot/grub/menu.lst file (.LST)
Ya, you are going to have to manually re-add the lines for the correct kernel to GRUB unfortunately, if you screw up you have to start all over again, so your best bet is to ask on this forum rather than attempt it yourself.

---

### Post by sgissinger on 2008-05-04
I tried to copy my menu.lst file with 3 different live CD distros and I still cannot do it. I am able to read it, but I cannot copy it in my Windows partition (from which I'm writing this), nor in a USB key even if I I have writing permissions or if I'm in su mode.
How can I post you the menu.lst file ?
I have Windows and hardy heron on the same disk.

---

### Post by TeoBigusGeekus on 2008-05-04
[http://www.fs-driver.org/]("http://www.fs-driver.org/")

Install ifs on window$ and post us the contents of the file from there.

---

### Post by sgissinger on 2008-05-04
OK so I finally copied my menu.lst file to my usb thanks to backtrack's auto root login. Thanks for your patience, I'm quite a newbie in unix... Here it is :

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
default		2

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
#timeout		10

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
# kopt=root=UUID=59acbccf-8a74-44f1-b8e4-7a98cdd41688 ro

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
# defoptions=splash vga=791 quiet

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
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-server
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-server root=UUID=59acbccf-8a74-44f1-b8e4-7a98cdd41688 ro splash vga=791 quiet
initrd		/boot/initrd.img-2.6.24-16-server
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-server (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-server root=UUID=59acbccf-8a74-44f1-b8e4-7a98cdd41688 ro single
initrd		/boot/initrd.img-2.6.24-16-server

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

---

### Post by TeoBigusGeekus on 2008-05-04
Startup manager has unfortunately deleted the other kernel entries...
You have to reinstall grub. I hope that this link will help you
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

It's for recovering grub after a window$ installation, but it applies to your case as well...

---

### Post by jocko on 2008-05-04
Instead of reinstalling grub, there is another thing you can do.
Reboot your computer, and when you get the boot menu, highlight the first option and press "e" to edit.
Now you will see this screen:


```
root        (hd0,1)
kernel        /boot/[COLOR=Red]vmlinuz-2.6.24-16-server[/COLOR] root=UUID=59acbccf-8a74-44f1-b8e4-7a98cdd41688 ro splash vga=791 quiet
initrd        /boot/[COLOR=Red]initrd.img-2.6.24-16-server[/COLOR]
quiet
```Highlight the second line (kernel), press "e" again to edit. Change the filename of the "vmlinuz.." file to one that corresponds to a kernel that works (probably just "-generic" instead of "-server"). When you changed it, press enter.
Do the same for the third line (initrd). When you are done, press b to boot.
Note that you have to change the file names to files that actually exists.
Check which files you have in your /boot directory before you start.

These changes are not permanent, but they will allow you to boot up and fix it from within your ubuntu. Undo whatever it was you did to cause this, and make sure you uninstall the server kernel and whatever kernel you don't want to keep.

---

### Post by sgissinger on 2008-05-05
Thanks, it works fine now. I replaced the kernel by 2.6.22-14-generic, after I checked my /boot directory.
I had already modified the kernel load name, but, I had forgotten to replace -server with -generic.
I have reset GRUB's settings to defaultin SUM, and now I get the 7.10 loading splash (a bar filling itself), which is perfect because I hated to see booting scripts after the logo (8.04).
Thanks again for your time, I shall not forget it.

---

