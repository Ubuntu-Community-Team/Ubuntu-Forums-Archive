---
title: "[SOLVED] Boot Menu"
date: 2008-06-25
forum: General Help
---

### Post by BurkeKnight on 2008-06-25
I am running dual boot, XP and Ubuntu.

I want XP as my default, since there is someone else who uses the XP side, and has no interest in the Ubuntu side.

Problem, I tried both KGrubEditor and StartupManager, and they both show XP as the default, yet, it still loads Ubuntu as the default.

Any ideas on why?

---

### Post by VMC on 2008-06-25
> **BurkeKnight said:**
> I am running dual boot, XP and Ubuntu.

I want XP as my default, since there is someone else who uses the XP side, and has no interest in the Ubuntu side.

Problem, I tried both KGrubEditor and StartupManager, and they both show XP as the default, yet, it still loads Ubuntu as the default.

Any ideas on why?

You could maybe force Statupmanager to change by unticking and then ticking the XP as default.

Dump the contents of menu list from a Terminal:

```
cat /boot/grub/menu.lst
```

Then we can see what's happening. You can check the option default in that file.

---

### Post by BurkeKnight on 2008-06-25
After using startupmanager, this is my menu.lst:



```
default 6
timeout 10

title Ubuntu 8.04, kernel 2.6.24-19-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=88aa9fe4-1d0b-4b8d-9980-0b2ef83f059d ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=88aa9fe4-1d0b-4b8d-9980-0b2ef83f059d ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04, kernel 2.6.22-14-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=88aa9fe4-1d0b-4b8d-9980-0b2ef83f059d ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=88aa9fe4-1d0b-4b8d-9980-0b2ef83f059d ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 8.04, memtest86+
root (hd0,4)
kernel /boot/memtest86+.bin

title Other operating systems:

title Microsoft Windows XP Professional
root (hd0,0)
chainloader +1
savedefault
makeactive
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
# kopt=root=UUID=88aa9fe4-1d0b-4b8d-9980-0b2ef83f059d ro

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

```

---

### Post by Xgen on 2008-06-25
Try Default '5'. Grub starts with '0' as the first choice.

---

### Post by BurkeKnight on 2008-06-25
Ok, that did it. :)

Thank you.

Oh, is there a way to stop it from wanting to do the Routine Disk Check during booting? I keep hitting skip, but it keeps wanting to do it. I'd rather it not do it at boot up like that.

---

### Post by pmlxuser on 2008-06-25
> **BurkeKnight said:**
> Ok, that did it. :)

Thank you.

Oh, is there a way to stop it from wanting to do the Routine Disk Check during booting? I keep hitting skip, but it keeps wanting to do it. I'd rather it not do it at boot up like that.

It usually do a disk check if you somehow shut the system abnormally so if you let it do the disk checking (ie don't skip), It will stop bothering you after that..:)

---

