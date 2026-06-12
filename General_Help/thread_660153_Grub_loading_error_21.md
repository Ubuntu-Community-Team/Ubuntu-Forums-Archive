---
title: "Grub loading error 21"
date: 2008-01-06
forum: General Help
---

### Post by kstelzer on 2008-01-06
Hi,

I know there are a lot of posts regarding this problem,unfortunately I cant seem to find an answer that is helpful.  I recently installed ubuntu 7.10 from the live cd using the install shortcut on the desktop.  I went through the steps and did a guided use entire disk at the partition step.  It said it would partition /dev/sda1 as ext3 at mount point /media/sda1 and also partition /dev/sda5 as swap.  Hitting the advanced button it also said it would install bootloader on hd0.  It installs correctly and using the live cd I am able to see the hard disk all configured, This is how I am able to see the grub menu.lst file.  The file looks like this:


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
# kopt=root=UUID=c9897a31-9325-41f6-8c60-9c04882fe6d5 ro

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
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c9897a31-9325-41f6-8c60-9c04882fe6d5 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c9897a31-9325-41f6-8c60-9c04882fe6d5 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

When I reboot, taking out the live cd and booting from the hard disk, I receive an error 21 when grub tries to load.  Seeing as how I am a new user, I do not know how to read or be able to verify the information in the menu.lst is correct.  Can anyone help me understand what I should do to try and fix this problem?  Is it strictly a grub problem or should I be looking deeper into a possible bios problem and update accordingly?

---

### Post by articpenguin on 2008-01-06
[http://ubuntuforums.org/showthread.php?t=62717]("http://ubuntuforums.org/showthread.php?t=62717")

---

### Post by kstelzer on 2008-01-06
Thanks for the reply, but the links you gave me are posts I have already looked at, and they don't really apply to me.  I do not have windows, this is a clean install of ubuntu and it seems to be having problems.  Shouldn't the install automatically detect and install grub on the correct volume/drive.  I really am new to this and I don't understand how it coundn't find something it just installed.  I only have one hard disk.  I am not dual booting.

---

### Post by kstelzer on 2008-01-06
So after researching my particular motherboard with this problem (Asus P5B Deluxe)  I found out that this is a known bug and I needed to update the bios.  So the ubuntu installer did everything correctly, it was the bios that didnt work properly.  I hope this will help any other new people out there.

---

