---
title: "Triple boot grub question"
date: 2007-04-23
forum: General Help
---

### Post by redwdc on 2007-04-23
I'm triple booting to ubuntu/kubuntu/XP (DOS and XP on the XP boot manager).
I've gotten the following grub menu.lst to work.  Now I'd like to know what
could go wrong with it, i.e., will I have any problems with a kernel upgrades,
or will it cause any data loss problems if I (God forbid) crash.

```

<snip>

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
# kopt=root=UUID=8b8ccc34-424d-4c07-8364-7d9eff9ab5b3 ro
# kopt=root=UUID=e94fef3c-c061-4a59-91db-566d2f1b12db ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic (gnome on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e94fef3c-c061-4a59-91db-566d2f1b12db ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (gnome on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e94fef3c-c061-4a59-91db-566d2f1b12db ro single 
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+ (gnome on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
quiet

title		Ubuntu, kernel 2.6.20-15-generic (kde on /dev/sdb2)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8b8ccc34-424d-4c07-8364-7d9eff9ab5b3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (kde on /dev/sdb2)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8b8ccc34-424d-4c07-8364-7d9eff9ab5b3 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+ (kde on /dev/sdb2)
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones. * Other operating systems *
title		-----------------------:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		DOS 7.10 and Win XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

red

---

