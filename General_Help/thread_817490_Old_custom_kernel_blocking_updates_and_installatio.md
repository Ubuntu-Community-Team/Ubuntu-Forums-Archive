---
title: "Old custom kernel blocking updates and installation of packages"
date: 2008-06-03
forum: General Help
---

### Post by Belial on 2008-06-03
Hi all, 

I had a custom kernel installed a while ago which i no longer needed, so removed it all from grub and /boot and /usr/lib/modules/{kernel version}-dave

the suffix -dave was added to the end of the kernel to identify it.

It has been removed for over a month without issue, however when going to update today, (Edit: One of the updates is linux-restricted-modules which would be why this didnt manafest until now) i was greeted with 

```

root@sophie:/boot# apt-get upgrade
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

```

when doing as it suggests

```

root@sophie:/boot# dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.25.4-dave
Cannot find /lib/modules/2.6.25.4-dave
update-initramfs: failed for /boot/initrd.img-2.6.25.4-dave
dpkg: subprocess post-installation script returned error exit status 1
root@sophie:/boot#

```

The contents of /boot
```

root@sophie:/boot# ls 
abi-2.6.24-16-generic             initrd.img-2.6.24-17-generic.bak
abi-2.6.24-17-generic             memtest86+.bin
config-2.6.24-16-generic          System.map-2.6.24-16-generic
config-2.6.24-17-generic          System.map-2.6.24-17-generic
grub                              vmlinuz-2.6.24-16-generic
initrd.img-2.6.24-16-generic.bak  vmlinuz-2.6.24-17-generic
root@sophie:/boot# 

```

Contents of /boot/grub/menu.lst
```

root@sophie:/boot# cat grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# kopt=root=UUID=576a599a-8fa0-472e-80bc-abff8421f597 ro

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

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=576a599a-8fa0-472e-80bc-abff8421f597 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=576a599a-8fa0-472e-80bc-abff8421f597 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=576a599a-8fa0-472e-80bc-abff8421f597 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=576a599a-8fa0-472e-80bc-abff8421f597 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

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
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows recovery
root		(hd0,1)
savedefault
chainloader	+1

root@sophie:/boot# 

```

Under advice from someone in #ubuntu this took place to no avail as well
```
root@sophie:/boot# update-initramfs -v -k all -u
Available versions:  2.6.25.4-dave
Execute: /usr/sbin/update-initramfs -u -k "2.6.25.4-dave" -b /boot -v -t
update-initramfs: Generating /boot/initrd.img-2.6.25.4-dave
Cannot find /lib/modules/2.6.25.4-dave
update-initramfs: failed for /boot/initrd.img-2.6.25.4-dave
root@sophie:/boot# update-initramfs -v -k all -c
Available versions:  2.6.25.4-dave
Execute: /usr/sbin/update-initramfs -c -k "2.6.25.4-dave" -b /boot -v -t
update-initramfs: Generating /boot/initrd.img-2.6.25.4-dave
Cannot find /lib/modules/2.6.25.4-dave
update-initramfs: failed for /boot/initrd.img-2.6.25.4-dave
root@sophie:/boot# 

```


Any help would be appreciated, this ones really got me at a loss, seems that something somewhere is still referencing the old kernel and im not familiar with the Debian/Ubuntu way of things

---

### Post by Belial on 2008-06-07
This has been revolved with the new kernel revision being released, however if anyone could give any more information as to why it happened in the first place would be appreciated

---

