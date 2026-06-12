---
title: "Kernel 2.6.24-17-generic and 2.6.24-16-generic"
date: 2008-05-31
forum: General Help
---

### Post by reyhan on 2008-05-31
Hello i just finished update my Ubuntu and theres a kernel update
and this is the output of /boot/grub/menu.lst

```
# Splashimage line added by kubuntu-grub-splashimages package
splashimage=(hd0,0)/boot/grub/splashimages/KUBUNTU_splashscreen_blue_neon_logo_03.xpm.gz

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
timeout		3

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
# kopt=root=UUID=65a268a0-df7a-44fd-b8ab-6d1658f9ec52 ro

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

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=65a268a0-df7a-44fd-b8ab-6d1658f9ec52 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=65a268a0-df7a-44fd-b8ab-6d1658f9ec52 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=65a268a0-df7a-44fd-b8ab-6d1658f9ec52 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=65a268a0-df7a-44fd-b8ab-6d1658f9ec52 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

and theres a > 
title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=65a268a0-df7a-44fd-b8ab-6d1658f9ec52 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

and > title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=65a268a0-df7a-44fd-b8ab-6d1658f9ec52 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

and can i remove the kernel 2.6.24-16?

---

### Post by Dougie187 on 2008-05-31
Yes, or to be more "safe" you can just comment it out. Just in case you need to use it again, then all you would need to do is uncomment it.

Just prepend all the lines with #

That should take care of it.

---

### Post by reyhan on 2008-05-31
But what happen if i remove the 2.6.24-16
is it safe?

---

### Post by Dougie187 on 2008-05-31
Yeah it should be fine. If you remove it all together, you might what to remove that kernel from your system. Because you won't be able to access it anymore, and it takes up space. I think a good practice is to keep the current and the previous kernel on your system though. So I would say, keep 16 and 17 for now, just comment out 16 incase you need it. Then when 18 comes out, remove 16 altogether.

This is just my opinion though, you can do what ever you want. So if you want to get rid of 16, that is fine, just remember to remove the kernel from your system as well.

---

### Post by Nepherte on 2008-05-31
A useful option in /boot/grub/menu.lst is 'howmany'
Somewhere in the file should say '#howmany=all', just change that to '#howmany=1'. The entries in the file will be kept, but upon booting, you will only see one kernel to boot from.

---

### Post by VMC on 2008-05-31
A thought just occurred to me. Recently there was an update that changed the kernel and subsequently I wasn't able to run a program. Thinking about it the fix was to patch the kernel. If I had use the old kernel I would have known that was the case. So maybe there is a use for the old kernel. It doesn't take up much space anyway.

---

### Post by meierfra. on 2008-06-01
> So maybe there is a use for the old kernel.

That's why I use "howmany=2". Keeps  the Grub Menu reasonable clean and I still have  my old kernel after a kernel update.

---

