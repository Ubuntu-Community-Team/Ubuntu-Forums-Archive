---
title: "GRUB question: booting Feisty + Edgy + WinXP"
date: 2007-03-11
forum: General Help
---

### Post by MeneK on 2007-03-11
Hi all,
I installed Feisty in one of my free partitions. Everything is working right just now, as the Feisty installer detected the other O.S., but I'm afraid that since the Edgy GRUB setup knows nothing about the new ubuntu I could lose access to Feisty if there is a kernel update for Edgy.

¿How can I configure GRUB to be able to boot the 3 O.S (Feisty, Edgy and XP) on my machine, not losing the setup if there is an Edgy kernel update?

Windows XP is on /dev/sda1 (hd0,0)
Ubuntu Edgy is on /dev/sda3 (hd0,2)
Ubuntu Feisty is on /dev/sda6 (hd0,5)

And this is my current menu.lst:

```

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
# kopt=root=UUID=7c6faf15-b783-48f8-8d89-cacde25aeb0d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
# defoptions=quiet splash vga=795

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

title		Ubuntu, kernel 2.6.20-9-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-9-generic root=UUID=7c6faf15-b783-48f8-8d89-cacde25aeb0d ro quiet splash vga=795
initrd		/boot/initrd.img-2.6.20-9-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-9-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-9-generic root=UUID=7c6faf15-b783-48f8-8d89-cacde25aeb0d ro single
initrd		/boot/initrd.img-2.6.20-9-generic

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu, kernel 2.6.17-11-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=cb9b4859-9d75-49e2-b48e-f607cbc7c16b ro splash vga=795 
initrd		/boot/initrd.img-2.6.17-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu, kernel 2.6.17-11-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=cb9b4859-9d75-49e2-b48e-f607cbc7c16b ro single 
initrd		/boot/initrd.img-2.6.17-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu, memtest86+ (on /dev/sda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot


```

Thanks!

---

### Post by Herman on 2007-03-11
```
## ## End Default Options ##

title        Ubuntu, kernel 2.6.20-9-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.20-9-generic root=UUID=7c6faf15-b783-48f8-8d89-cacde25aeb0d ro quiet splash vga=795
initrd        /boot/initrd.img-2.6.20-9-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-9-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.20-9-generic root=UUID=7c6faf15-b783-48f8-8d89-cacde25aeb0d ro single
initrd        /boot/initrd.img-2.6.20-9-generic

title        Ubuntu, memtest86+
root        (hd0,5)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


[B][COLOR=Red]# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title        Ubuntu Edgy Eft, configfile boot (on /dev/sda3)
configfile    (hd0,2)/boot/grub/menu.lst
[/COLOR][/B]

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```Hello MeneK,
You just need to delete the direct kernel booting commands and replace them with a 'configfile' boot command.
The 'configfile' command doesn't boot Edgy Eft, instead it will give you the Grub menu from Edgy Eft and you can then boot from that. 
That means you will be booting from the menu.lst file that Edgy's own automagic kernels list will keep up to date with the latest kernels without you needing to do anything manually.

If you want to make the arrangement a little fancier, install a different [splashimage]("http://users.bigpond.net.au/hermanzone/p15.htm#splash") in each operating system. 
Another idea is to make a similar configfile entry in your Edgy menu.lst to give you the option of returning to your Fiesty grub menu again.

Enjoy!
Regards, Herman :)

---

### Post by MeneK on 2007-03-11
Thanks, Herman! 
Everything works fine now, even the splashimage in the main menu.lst.

The only tricky thing is that the "savedefault" line in some of  the Edgy menu.lst options has to be removed or it won't boot.

Thanks again!

---

