---
title: "No Splash Screen"
date: 2008-05-01
forum: General Help
---

### Post by griehl2490 on 2008-05-01
I do not have a splash screen anymore. I'm not sure as to what happened/what I did but I don't have a splash screen...it just shows a black screen with white text of what my CPU is doing.

---

### Post by CREEPING DEATH on 2008-05-01
You're lucky, I have to do that manually after I install, I prefer it that way so I know what's going on.

CD

---

### Post by T-Virus on 2008-05-01
By splash screen you mean the one which shows up as system is starting up after login?

---

### Post by njparton on 2008-05-01
What's your graphics hardware? Are you using restricted drivers?
 
I must admit that I too prefer to see what's going on.

---

### Post by Nepherte on 2008-05-01
> **T-Virus said:**
> By splash screen you mean the one which shows up as system is starting up after login?
I think he means when booting.

To show the bootsplash, open up /boot/grub/menu.lst
```
sudo gedit /boot/grub/menu.lst
```
There should be some lines similar to this:
```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=6c0f7119-85e4-442a-8ae2-83b0b5748140 ro quiet **splash**
initrd          /boot/initrd.img-2.6.22-14-generic
quiet
```
At the end of kernel line, the word splash should be there. If not, add it.

---

### Post by -error on 2008-05-06
may i post here to not create additional topics? thanks :-)

i wonder how to change refresh rate of bootsplash's video mode. when system is booting i see garbage on monitor (btw, it is TFT Samsung 980N) and it (monitor) complains that inappropriate video mode set suggesting to change it to 1280x1024@60Hz.
but to do that? i can only switch to 1024x768 by setting vga="idonotremeberexactlywhat".

---

### Post by NoPoChris on 2008-06-09
I wanted to change my bootsplash, so I found out how to do that and I did it. Then I decided that I didn't want to have a bootsplash, so I found out how to do that (edit something in menu.list) and I did it. Now I want to have the bootsplash back but I can't get it to come back.

```
sudo update-alternatives --config usplash-artwork.so
```
Gives me:

```
There are 3 alternatives which provide `usplash-artwork.so'.

  Selection    Alternative
-----------------------------------------------
 +        1    /usr/local/lib/usplash/minimalastic.so
          2    /usr/lib/usplash/usplash-theme-kubuntu.so
*         3    /usr/lib/usplash/usplash-theme-ubuntu.so

Press enter to keep the default[*], or type selection number:
```

So I choose the one I want to use and it tells me I'm using that one. But if I reboot there's no splash.

```
sudo gedit /boot/grub/menu.lst
```
Is:
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
# kernel	/vmlinuz root=/dev/hda2 ro quiet splash
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
# kopt=root=UUID=303af1ec-b3b3-4c81-b81d-422564904444 ro

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
# defoptions=verbose splash

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

title		Ubuntu 8.04, kernel 2.6.24-18-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-rt root=UUID=303af1ec-b3b3-4c81-b81d-422564904444 ro verbose splash
initrd		/boot/initrd.img-2.6.24-18-rt
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-rt root=UUID=303af1ec-b3b3-4c81-b81d-422564904444 ro single
initrd		/boot/initrd.img-2.6.24-18-rt

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=303af1ec-b3b3-4c81-b81d-422564904444 ro verbose splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=303af1ec-b3b3-4c81-b81d-422564904444 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-17-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-rt root=UUID=303af1ec-b3b3-4c81-b81d-422564904444 ro verbose splash
initrd		/boot/initrd.img-2.6.24-17-rt
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-rt root=UUID=303af1ec-b3b3-4c81-b81d-422564904444 ro single
initrd		/boot/initrd.img-2.6.24-17-rt

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=303af1ec-b3b3-4c81-b81d-422564904444 ro verbose splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=303af1ec-b3b3-4c81-b81d-422564904444 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-rt root=UUID=303af1ec-b3b3-4c81-b81d-422564904444 ro verbose splash
initrd		/boot/initrd.img-2.6.24-16-rt
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-rt root=UUID=303af1ec-b3b3-4c81-b81d-422564904444 ro single
initrd		/boot/initrd.img-2.6.24-16-rt

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=303af1ec-b3b3-4c81-b81d-422564904444 ro verbose splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=303af1ec-b3b3-4c81-b81d-422564904444 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=303af1ec-b3b3-4c81-b81d-422564904444 ro verbose splash
initrd		/boot/initrd.img-2.6.22-14-rt
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=303af1ec-b3b3-4c81-b81d-422564904444 ro single
initrd		/boot/initrd.img-2.6.22-14-rt

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```
sudo update-grub
```
Says:
```
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
**Searching for splash image ... none found, skipping ...**
Found kernel: /boot/vmlinuz-2.6.24-18-rt
Found kernel: /boot/vmlinuz-2.6.24-18-generic
Found kernel: /boot/vmlinuz-2.6.24-17-rt
Found kernel: /boot/vmlinuz-2.6.24-17-generic
Found kernel: /boot/vmlinuz-2.6.24-16-rt
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/vmlinuz-2.6.22-14-rt
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
```

And
```
sudo gedit /etc/usplash.conf
```

Says:
# Usplash configuration file
xres=1280
yres=1280

These seem to be the commands that are related to the bootsplash. I feel that something in menu.list is not the way it should be, but I don't know exactly what. Or maybe I'm going about this all wrong. I've been trying to figure this out for two days now...Please help.

---

