---
title: "bug in 686 kernel package?"
date: 2005-10-18
forum: General Help
---

### Post by mcframe on 2005-10-18
Hi, i'm trying to run the 2.6.12-9-686 kernel with the (k)ubuntu usplash artwork which unfortunately does not bring any graphical effect because insmod complains that /lib/modules/2.6.12-9-686/initrd/vesafb.ko is mising or not accessible although the file is in place. I know that this is partly caused by my grub setting: Code: vga=0x031a but exactly the same setting is working with the 2.6.12-9-K7 kernel on a different machine without probs. Can someone please check and confirm the same poblem to find out if it's a bug within the kernel package build. cheers mcframe

---

### Post by seldenthuis on 2005-10-18
I have exactly the same kernel, but the vga option works just fine. The error message you get seems to indicate that you're trying to use the vesafb framebuffer. Usplash uses the vga16fb framebuffer, so there's a conflict there. You may have to change some kernel options in /boot/grub/menu.list.

My menu.list looks like this:

```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

splashimage (hd0,0)/boot/grub/splashimages/ubuntu.xpm.gz

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.12-9-686
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-686 root=/dev/hda1 ro quiet splash vga=0x31B
initrd          /boot/initrd.img-2.6.12-9-686
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-686 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-686 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.12-9-686
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by mcframe on 2005-10-19
[QUOTE=seldenthuis]I have exactly the same kernel, but the vga option works just fine. The error message you get seems to indicate that you're trying to use the vesafb
[/QUOTE]
There is no reference to vesafb I can see.

[QUOTE=seldenthuis]
My menu.list looks like this:
[/QUOTE]
Thank you for this information, I've updated my menu.list (from vga=0x031a to vga=0x31b) but unfortunately the error remains.

Here is my menu.list
```

# menu.lst - See: grub(8), info grub, update-grub(8)
#<sniped>
default		saved

timeout		3


title		Ubuntu, kernel 2.6.12-9-686 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-686 root=/dev/hda2 ro quiet splash vga=0x31B
initrd		/boot/initrd.img-2.6.12-9-686
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-686 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-686 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.12-9-686
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash vga=0x31B
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.10-5-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
# vga=0x031a
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
    root (hd0,0)
    chainloader +1


```

Any other idea?

---

### Post by dakira on 2005-10-19
Hi,

It is not quite true that usplash uses vga16fb only, there is a script that checks for the vga setting in menu.lst and decides to either use vga16fb or vesafb.

open the 
/usr/share/initramfs-tools/scripts/init-top/usplash script and change line 41
from
insmod /lib/modules/`uname -r`/initrd/vesafb.ko
to
insmod /lib/modules/`uname -r`/kernel/drivers/video/vesafb.ko

that should take care of the error.

A question on my own behalf: How do I activate usplash anyway? I have all the packages installed but nothing happens. I get no error messages, no sign of usplash anywhere. Not that I'd need usplash but I was kind of looking forward to it when I heard it's integrated in Breezy.

---

### Post by seldenthuis on 2005-10-19
After upgrading to Breezy run:

sudo dpkg-reconfigure usplash
sudo dpkg-reconfigure linux-image-`uname -r`

This will get usplash working and maybe also take care of the vesafb problem.

PS: vga=0x31a should work as well. It's just that vga=0x31b gives you more colors (16M instead of 64k).

---

### Post by mcframe on 2005-10-19
Hi,
thanks a lot for your support :-) 
I have followed both suggestions above and it worked right away.
Kubuntu feels just a little nicer with its new splash screeen.

Cheers

---

### Post by dakira on 2005-10-19
@seldenthuis
thanks alot.. now everything works for me.

---

