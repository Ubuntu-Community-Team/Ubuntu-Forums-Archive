---
title: "[SOLVED] Kernel Panic error (Dapper 6.06 LTS)"
date: 2007-04-13
forum: General Help
---

### Post by pcolamar on 2007-04-13
Hi there,

I have done some change to my HD configuration and now I am getting a strange Kernel Panic error.
Beforehand, let me say that is strongly possible that Ubuntu was in hibernation when I did all the changes via WinXP. The changes to the HD consisted changing all but the Win XP partition from primary to logical, consequentially all the partitions have a different hdaX number.
Important to note that the old SWAP has moved from hda3 -> hda7 now.

---------- The message on the screen when booting is:

...
...
Begin. Running /scripts/local-premount.....
[17179574.9760000] Attempting manual resume
[17179574.9760000] attempt to access beyond end of device
[17179574.9760000] hda3: rw=16, want=8, limit=2
[17179574.9760000] Kernel panic - not syncing:I/O error reading memory image
[17179574.9760000]
-------------------------------------

then the laptop hangs, no keystroke has any effect and I have to turn it off.

I have tried to locate the /scripts directory without success (maybe it's a symbolic link !).
Any suggestion ?
If, as I think, it's an attempt to resume from a Swap area not existing any longer, how can delete the resume flag and let it boot normally?

I have already changed the fstab file correcting all the /dev/hdaX definitions
Thanks

Palmer

---

### Post by pointone on 2007-04-14
The /scripts directory is included in your initrd image. I doubt that's the issue, though; I agree it sounds like a resume gone bad.

When the system is about to start, hit escape to enter the GRUB boot menu. Next, hit 'e' to edit the boot options for your default configuration. Select the kernel and hit 'e' again to edit the kernel options. Remove the resume option; usually /dev/hda5 (but probably /dev/hda3 in your case). Hit enter to save the changes and then 'b' to boot.

If this works, you can make the change permanent by writing to your /boot/grub/menu.lst file.

---

### Post by pcolamar on 2007-04-14
Pointone,
  I tried your suggestion but there is no 'resume' option on the kernel row.
Here below my menu.lst file . You may see that I have Feisty and Dapper on the HD.
Festy is not working properly (but that's another issue) , I am trying to boot back to dapper 2.6.15.28 that worked fine before I splitted the hd to create space for Feisty.
I am starting thinking to reinstall from CD Dapper and that's it !
Thanks
Palmer


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
# kopt=root=UUID=b001b56c-817a-4184-98be-2783d32aec0c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

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

title		Ubuntu, kernel 2.6.20-12-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-12-generic root=UUID=b001b56c-817a-4184-98be-2783d32aec0c ro quiet splash
initrd		/boot/initrd.img-2.6.20-12-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-12-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-12-generic root=UUID=b001b56c-817a-4184-98be-2783d32aec0c ro single
initrd		/boot/initrd.img-2.6.20-12-generic

title		Ubuntu, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu, kernel 2.6.15-28-k7 (on /dev/hda6)
root		(hd0,5)
# kernel		/boot/vmlinuz-2.6.15-28-k7 root=/dev/hda6 ro quiet splash 
kernel		/boot/vmlinuz-2.6.15-28-k7 root=/dev/hda6 ro noresume
initrd		/boot/initrd.img-2.6.15-28-k7
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu, kernel 2.6.15-28-k7 (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-28-k7 root=/dev/hda6 ro single 
initrd		/boot/initrd.img-2.6.15-28-k7
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu, kernel 2.6.15-27-k7 (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-27-k7 root=/dev/hda6 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-27-k7
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu, kernel 2.6.15-27-k7 (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-27-k7 root=/dev/hda6 ro single 
initrd		/boot/initrd.img-2.6.15-27-k7
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu, memtest86+ (on /dev/sda6)
root		(hd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by pointone on 2007-04-14
Have you tried *adding* a resume line, in that case? Add 'resume=/dev/hda7' to the kernel options and try again.

---

### Post by pcolamar on 2007-04-15
And there you were right, Pointone !!!

the 'resume=.....' did the magic.

I have got Dapper back.

Thanks

Palmer

---

