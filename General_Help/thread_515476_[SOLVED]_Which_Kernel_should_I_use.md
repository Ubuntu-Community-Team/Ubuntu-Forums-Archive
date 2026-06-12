---
title: "[SOLVED] Which Kernel should I use"
date: 2007-08-02
forum: General Help
---

### Post by ashdezign on 2007-08-02
Hi, I am still a noob on linux but working hard to learn my way around.

I was exploring my grub the other day, did not change anything but am considering doing so.

The reason is that it seems as if my default kernel to load into is the  low latency kernel. I seem to remember reading somewhere that the low latency kernel is really only for special cases.

I am on a Dell Inspiron E1505 running ubuntu studio with compiz fusion (dont know if that makes any difference)

I ran ```
gksudo gedit /boot/grub/menu.lst
``` from terminal to see what it says. I have made no changes and I am not experiencing any real problems, but I am wondering should I set the default kernel to the generic one? Would it give me better performance? Or should I leave it as is?

Below is the output from ```
gksudo gedit /boot/grub/menu.lst
``````
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=5d1eec54-40dc-4cab-be01-694ff1e74656 ro

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

## ## End Default Options ##

title        Ubuntu, kernel 2.6.20-16-lowlatency
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-16-lowlatency root=UUID=5d1eec54-40dc-4cab-be01-694ff1e74656 ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-lowlatency
quiet
savedefault

title        Ubuntu, kernel 2.6.20-16-lowlatency (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-16-lowlatency root=UUID=5d1eec54-40dc-4cab-be01-694ff1e74656 ro single
initrd        /boot/initrd.img-2.6.20-16-lowlatency

title        Ubuntu, kernel 2.6.20-16-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=5d1eec54-40dc-4cab-be01-694ff1e74656 ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=5d1eec54-40dc-4cab-be01-694ff1e74656 ro single
initrd        /boot/initrd.img-2.6.20-16-generic

title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=5d1eec54-40dc-4cab-be01-694ff1e74656 ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=5d1eec54-40dc-4cab-be01-694ff1e74656 ro single
initrd        /boot/initrd.img-2.6.20-15-generic

title        Ubuntu, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```Any thoughts anyone?

Thanks!

---

### Post by mcduck on 2007-08-02
Generic kernel is best for normal desktop use, as it balances better with many running applications. Low-latency kernel is made for audio use, and it gives more CPU time to the currently running program to allow lower latencies with CPU-intensive audio production tasks.

---

### Post by ashdezign on 2007-08-02
Thanks!

So in my situation where I normally have a lot of process running at the same time (email, web browser, open office, amorak, IM and so on) generic Kernel would probably be best?

How should I edit the grub/menu.lst?

change:
```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0
```to:

```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        2
```[COLOR=#000000]Is that about right?[/COLOR]

---

### Post by mcduck on 2007-08-02
> **ashdezign said:**
> Thanks!

So in my situation where I normally have a lot of process running at the same time (email, web browser, open office, amorak, IM and so on) generic Kernel would probably be best?

How should I edit the grub/menu.lst?

change:
```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0
```to:

```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        2
```[COLOR=#000000]Is that about right?[/COLOR]

Right, and right :D

---

### Post by ashdezign on 2007-08-02
Thanks!

---

### Post by walkerk on 2007-08-02
If you want a newer kernel give my [thread a look]("http://ubuntuforums.org/showthread.php?t=511974").. very simple and I use it on a Dell 6400/(1505)

---

### Post by ashdezign on 2007-08-02
walkerk: I will be giving it a try over the next few days, thanks!

First I want to see how the generic kernel plays before updating to a new one.

One question though, about how much space does each kernel take on the hard drive? Is running short on space an issue?

---

### Post by mcduck on 2007-08-02
> **ashdezign said:**
> walkerk: I will be giving it a try over the next few days, thanks!

First I want to see how the generic kernel plays before updating to a new one.

One question though, about how much space does each kernel take on the hard drive? Is running short on space an issue?

kernel image, kernel modules and headers together take something around 200MB so unless you are _really_ low on disk space there should be no problem. You can also uninstall old kernel versions with Synaptic after kernel updates if you don't use them any more and the latest kernel works fine for you.

(If you compile from your own kernel from source you'll need more than that, as you'll also get source code for everything and some additional stuff needed for compiling the kernel.)

---

