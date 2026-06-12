---
title: "Remove Hardy Heron from boot list"
date: 2008-05-25
forum: General Help
---

### Post by charlesbw on 2008-05-25
After upgrading to Hardy Heron, i now have a list of 3 OS during start up.  Except that two of these are both Hardy Heron and the first one on the list does not load ubuntu, how can i get it off that list so that only the one that actually loads ubuntu is left.  Any help is greatly appreciated.

---

### Post by 505 on 2008-05-25
Edit the file /boot/grub/menu.lst It is a normal text file. You can remove sections that you don't longer need. However, be careful, because if the file contains errors grub can not load some options, which can even lead to not being able to boot your computer.

---

### Post by drs305 on 2008-05-25
If you are unsure which portion to remove just post the results of the following and someone will show you which lines to remove:
```
cat /boot/grub/menu.lst
```

---

### Post by ibuclaw on 2008-05-25
> **drs305 said:**
> If you are unsure which portion to remove just post the results of the following and someone will show you which lines to remove:
```
cat /boot/grub/menu.lst
```
Although I recommend this command instead:
```
cat /boot/grub/menu.lst | grep -v "#" | uniq
```
It will produce a cleaner output for people to read.

Regards
Iain

[EDIT]
> I've seen it and really like it - even thought of stealing it - but since it's not what the user would see when he edits it I like the original.
+1
You've made a good point there.

Although I would argue that I'm sure the OP is smart enough to tell the difference.
But I can sympathise, because I do agree with reasoning point that the menu.lst file is "**needlessly**" imploded with comments.

But I'm glad you like it all the same :D

---

### Post by drs305 on 2008-05-25
> **tinivole said:**
> Although I recommend this command instead:
```
cat /boot/grub/menu.lst | grep -v "#" | uniq
```
It will produce a cleaner output for people to read.

Regards
Iain

Iain,

I've seen it and really like it - even thought of stealing it - but since it's not what the user would see when he edits it I like the original. ;-)

---

### Post by charlesbw on 2008-05-25
here it is:

> charles@charles-roomcpu:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=bde3525c-0659-45e6-81c7-72fc91354e4e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=bde3525c-0659-45e6-81c7-72fc91354e4e ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=bde3525c-0659-45e6-81c7-72fc91354e4e ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bde3525c-0659-45e6-81c7-72fc91354e4e ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bde3525c-0659-45e6-81c7-72fc91354e4e ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


---

### Post by charlesbw on 2008-05-25
also apparently i do not have the permission to save the file in grub...anyone know how i can fix that? thanks for the help so far guys.

---

### Post by drs305 on 2008-05-25
Added: you can run the following to make sure you are really running kernel 2.6.24-14, which is the kernel you will see on the menu if you follow the rest of this post.
```
uname -a
```

Using sudo will allow you to save the file. That file is owned by root so a normal user can't make changes to it without using 'sudo' powers.

Make a backup of your menu.lst:
```
sudo cp /boot/grub/menu.lst /boot.grub/menu.lst.orig

```
Open an editor to make the changes:
```
gksudo gedit /boot/grub/menu.lst

```

Delete the following just after the " **## ## End Default Options ##** " line. Keep the line in  bold type.
You can also just put comment symbols at the start of each line to prevent seeing this line on the menu. You could delete them later if you wish.
Note that this is the first reference you cited, although it is a more recent kernel than the one that will remain:
```

**## ## End Default Options ##**

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=bde3525c-0659-45e6-81c7-72fc91354e4e ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=bde3525c-0659-45e6-81c7-72fc91354e4e ro single
initrd /boot/initrd.img-2.6.24-16-generic

```

---

### Post by Old Marcus on 2008-05-25
I assume if you accidentally bugger this up and Grub doesn't load, you can still boot into a livecd?

---

### Post by drs305 on 2008-05-25
> **Old Marcus said:**
> I assume if you accidentally bugger this up and Grub doesn't load, you can still boot into a livecd?

Yes, but that was the reason for the cp line. If something gets messed up, you would delete the menu.lst file and rename the menu.list.orig back to menu.lst.  Of course, getting to a command line to do that isn't as easy as if you are already logged on.

Although it may not have worked in this case, if you are nervous about making changes to menu.lst you can change several of the options in System, Administration, Startup-Manager. If you don't have it, install it with:
```
sudo aptitude install startupmanager
```

---

### Post by charlesbw on 2008-05-25
thanks drs, i skipped ahead and did that.  but i did exactly what you said, thanks, now i feel more comfortable with a restart.

---

