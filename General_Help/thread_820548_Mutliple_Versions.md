---
title: "Mutliple Versions"
date: 2008-06-06
forum: General Help
---

### Post by Glock19_11 on 2008-06-06
I have installed Ubuntu 8.04 (dual booting with XP) on my Latitude D610. absolutely love it! I've noticed a lil glitch or bug. Some how when i get the option to select my OS each time computer restarts I have 3 versions of Ubuntu. Each has a safe mode and then there is a single memtest. The 3rd one i noticed came into existence when i put my computer in stand by. Before that i only had 2 versions now i have 3. I've put it in stand by before and not experienced this. 

Basically unless someone can tell me how to resolve this issue I'm looking at having to clean Ubuntu of my HD and do a clean install. 

help/suggestions/pointers anyone?

---

### Post by peakshysteria on 2008-06-06
As you can see I'm sure there are three different kernel versions where the newest and default is the latest with the highest version number. I'm not sure how you edit and remove older versions. This is not a bug.

---

### Post by jtrindle on 2008-06-06
You could remove the Grub menu options by hand, but it looks like you can remove the kernel packages for the previous versions of the kernel through Synaptic, and that will take the Grub menu options out.

It's good to leave at least one older, known-good kernel as well as the one you are currently using, just in case you run into a problem.

---

### Post by pedro_orange on 2008-06-06
If you don't like em take em out:

```
sudo nano -w /boot/grub/menu.lst
```

Here's mine:

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
# kopt=root=UUID=3fe9dc7d-ee53-4b38-bc76-9ca9147cd42b ro

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

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=3fe9dc7d-ee53-4b38-bc76-9ca9147cd42b ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=3fe9dc7d-ee53-4b38-bc76-9ca9147cd42b ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=3fe9dc7d-ee53-4b38-bc76-9ca9147cd42b ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=3fe9dc7d-ee53-4b38-bc76-9ca9147cd42b ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3fe9dc7d-ee53-4b38-bc76-9ca9147cd42b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3fe9dc7d-ee53-4b38-bc76-9ca9147cd42b ro single
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

```

---

### Post by Glock19_11 on 2008-06-06
what would i search in synaptic to find these kernals?

---

### Post by unixg33k on 2008-06-06
You'll have to edit your /boot/grub/menu.lst file and remove the additional entries.  Personally, I prefer to leave the options there in case of kernel problems.

---

### Post by pedro_orange on 2008-06-06
> **Glock19_11 said:**
> what would i search in synaptic to find these kernals?

Mate

Edit the file I linked above.

Just # out the sections you don't want to show on ur boot loader. Easy.

---

### Post by peakshysteria on 2008-06-06
> **pedro_orange said:**
> If you don't like em take em out:

```
sudo nano -w /boot/grub/menu.lst
```

Here's mine:

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
# kopt=root=UUID=3fe9dc7d-ee53-4b38-bc76-9ca9147cd42b ro

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

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=3fe9dc7d-ee53-4b38-bc76-9ca9147cd42b ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=3fe9dc7d-ee53-4b38-bc76-9ca9147cd42b ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=3fe9dc7d-ee53-4b38-bc76-9ca9147cd42b ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=3fe9dc7d-ee53-4b38-bc76-9ca9147cd42b ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3fe9dc7d-ee53-4b38-bc76-9ca9147cd42b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3fe9dc7d-ee53-4b38-bc76-9ca9147cd42b ro single
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

```

So then if I want to remove:

```
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3fe9dc7d-ee53-4b38-bc76-9ca9147cd42b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3fe9dc7d-ee53-4b38-bc76-9ca9147cd42b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

```

I just delete those lines in the grub menu??

I'm running singleboot and can't see this list at boot at all. Not even recovery mode. The countdown is three seconds I think. But my daughters machine (she's running dual boot) have the same list of kernels and win xp at boot. Is there a way to see a listing of my kernel(s) and recovery mode at boot with a single boot?

---

### Post by cygnine on 2008-06-07
> **peakshysteria said:**
> So then if I want to remove:

```
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3fe9dc7d-ee53-4b38-bc76-9ca9147cd42b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3fe9dc7d-ee53-4b38-bc76-9ca9147cd42b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

```

I just delete those lines in the grub menu??

Well, you should probably just comment them out (prepend lines with the # character) in case you want them later. In general you shouldn't change files for system functionality without being able to undo those changes. Note that this doesn't actually remove the kernel versions; it just doesn't give you the startup option booting with them.

> **peakshysteria said:**
> I'm running singleboot and can't see this list at boot at all. Not even recovery mode. The countdown is three seconds I think. But my daughters machine (she's running dual boot) have the same list of kernels and win xp at boot. Is there a way to see a listing of my kernel(s) and recovery mode at boot with a single boot?

If you look at the first few lines of pedro_orange's menu, there are lines that look like

```
default		0
timeout		10
#hiddenmenu

```

The first line shows the default OS number to boot into if no user input is given. The second gives the countdown time in the boot menu in seconds; I believe if you set the timeout to be 0, then the menu just loads default automatically. The third looks to be a directive to hide the menu. It's commented out above, so that menu is shown.

So if you want to enable a boot-up menu, I'd check:
1.) That your timeout is more than 0
2.) That the hiddenmenu directive is commented out.

---

### Post by jocko on 2008-06-07
Removing the grub entries is only a temporary fix.
Uninstall the older kernels, otherwise they will just come back next time grub gets reconfigured.
The packages are named linux-image-2.6.24-xy-generic (just search for linux-image to find them all). Make sure you keep the packages "linux-image" and "linux-image-generic" ( without any version numbers in their names).
Leave the one with the highest number, and if you want to be absolutely safe you can keep one more.

---

