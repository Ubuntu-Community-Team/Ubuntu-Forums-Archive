---
title: "can't boot windows!"
date: 2007-12-01
forum: General Help
---

### Post by linux noooob on 2007-12-01
ok so after having ubuntu installed i was thinking of playing a 3d game which does not work with wine  so i reinstalled windows to a 9.5 (10 gig in decimal) partition. but i can not load it!
my menu .list
>  
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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7447016a-ffc7-4afa-9640-a41d05482204 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7447016a-ffc7-4afa-9640-a41d05482204 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

and the results from sudo fdisk -l
> Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x34fe34fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5931    47640726   83  Linux
/dev/sda2            7207        7296      722925    5  Extended
/dev/sda3            5932        7206    10241437+   7  HPFS/NTFS
/dev/sda5            7207        7296      722893+  82  Linux swap / Solaris

Partition table entries are not in disk order


HELP!!!!

(note it is sda not hda)

---

### Post by bernied on 2007-12-01
Windows doesn't like not being on the first partition, but see how you go with this. You will need to add this to the end of your menu.lst file, which you will need to edit as root. So maybe use:
```
gksudo gedit /boot/grub/menu.lst
```
Then the new entry would look something like this:
```
title Windows
root (hd0,2)
makeactive
chainloader +1
```
This is assuming that its the sda3 partition that you want (because it's NTFS).
The makeactive command sets a 'bootable' flag on the partition table, which is currently set on the first partition (that * in the fdisk output). Windows needs this to be set, but linux does not. The chainloader command says to use the bootloader on the target partition (because grub cannot load windows directly, we have to use the windows bootloader).

If this doesn't work, we can try the swap command, which will fool windows into thinking that it is on the first partition. But try this first.

---

### Post by linux noooob on 2007-12-01
ok i did that but now it stays on boot of windows: > starting up but does nothing else-_-

---

### Post by bernied on 2007-12-01
How exactly did you 'reinstall windows'? If the install had completed, windows would have installed its own bootloader and made ubuntu unbootable. Did this happen?

---

### Post by Cresho on 2007-12-02
i must of spent a good 2 hours reading but i got mines to work.

here is it and read my explenation please!  it will help.

### END DEBIAN AUTOMAGIC KERNELS LIST
title		Windows XP-sp2
root (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1


hd2 is my sata 1 and not zero.  The "map" need to be in place becase windows refuses to be the second boot partition.  I placed the strings after "### END DEBIAN AUTOMAGIC KERNELS LIST" because if you but it before, grub will re-write and erase it from the menu.lst file loosing your windows boot.


just change the number 2 to 3 or 1.  this represents the sata drives.  even 4 if your curious.

---

### Post by linux noooob on 2007-12-02
> **Cresho said:**
> i must of spent a good 2 hours reading but i got mines to work.

here is it and read my explenation please!  it will help.

### END DEBIAN AUTOMAGIC KERNELS LIST
title		Windows XP-sp2
root (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1


hd2 is my sata 1 and not zero.  The "map" need to be in place becase windows refuses to be the second boot partition.  I placed the strings after "### END DEBIAN AUTOMAGIC KERNELS LIST" because if you but it before, grub will re-write and erase it from the menu.lst file loosing your windows boot.


just change the number 2 to 3 or 1.  this represents the sata drives.  even 4 if your curious.

thanks that makes sense ok so first i have to put it after the debain thing ok also it is sp1 and i reinstalled it by making a 10gb ntfs partition and then used a recovery cd to install it.

---

