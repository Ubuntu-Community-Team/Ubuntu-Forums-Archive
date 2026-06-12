---
title: "fix my grub"
date: 2007-11-10
forum: General Help
---

### Post by svtfmook on 2007-11-10
here's my menu.lst
```
# Splashimage line added by kubuntu-grub-splashimages package
splashimage=(hd0,1)/boot/grub/splashimages/KUBUNTU_splashscreen_blue_neon_logo_03.xpm.gz

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
# kopt=root=UUID=aa007f4f-36ec-412d-a246-308a52931e98 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

#title		Ubuntu, kernel 2.6.20-16-generic
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=aa007f4f-36ec-412d-a246-308a52931e98 ro quiet splash rootflags=data=writeback
#initrd		/boot/initrd.img-2.6.20-16-generic
#quiet
#savedefault

#title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=aa007f4f-36ec-412d-a246-308a52931e98 ro single
#initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=aa007f4f-36ec-412d-a246-308a52931e98 ro quiet splash rootflags=data=writeback
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=aa007f4f-36ec-412d-a246-308a52931e98 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu, kernel 2.6.20-15-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=c66b6cd2-eee9-4c2c-9af1-74030ff3edd4 ro quiet splash rootflags=data=writeback
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=c66b6cd2-eee9-4c2c-9af1-74030ff3edd4 ro single 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

now, the problem i have, is there's 2 lists of options.  you'll see that i commented out one of the options, because its on the top, and will auto select it, however, it fails.  anyhow, what i want is either only the one that works to display, or just auto boot into the one that works without going into the grub menu (no longer dual booting on 1 drive).

---

### Post by -grubby on 2007-11-10
the first step is to post this in the right sub -forum

---

### Post by svtfmook on 2007-11-10
which would that be?

---

### Post by -grubby on 2007-11-10
> **svtfmook said:**
> which would that be?

if you can't find a specific help forum,use the general help forum

---

### Post by Nano Geek on 2007-11-10
> **svtfmook said:**
> here's my menu.lst
```
# Splashimage line added by kubuntu-grub-splashimages package
splashimage=(hd0,1)/boot/grub/splashimages/KUBUNTU_splashscreen_blue_neon_logo_03.xpm.gz

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
timeout        10

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
# kopt=root=UUID=aa007f4f-36ec-412d-a246-308a52931e98 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

#title        Ubuntu, kernel 2.6.20-16-generic
#root        (hd0,1)
#kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=aa007f4f-36ec-412d-a246-308a52931e98 ro quiet splash rootflags=data=writeback
#initrd        /boot/initrd.img-2.6.20-16-generic
#quiet
#savedefault

#title        Ubuntu, kernel 2.6.20-16-generic (recovery mode)
#root        (hd0,1)
#kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=aa007f4f-36ec-412d-a246-308a52931e98 ro single
#initrd        /boot/initrd.img-2.6.20-16-generic

title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=aa007f4f-36ec-412d-a246-308a52931e98 ro quiet splash rootflags=data=writeback
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=aa007f4f-36ec-412d-a246-308a52931e98 ro single
initrd        /boot/initrd.img-2.6.20-15-generic

title        Ubuntu, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu, kernel 2.6.20-15-generic (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=c66b6cd2-eee9-4c2c-9af1-74030ff3edd4 ro quiet splash rootflags=data=writeback
initrd        /boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=c66b6cd2-eee9-4c2c-9af1-74030ff3edd4 ro single 
initrd        /boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu, memtest86+ (on /dev/sda1)
root        (hd0,0)
kernel        /boot/memtest86+.bin  
savedefault
boot

```now, the problem i have, is there's 2 lists of options.  you'll see that i commented out one of the options, because its on the top, and will auto select it, however, it fails.  anyhow, what i want is either only the one that works to display, or just auto boot into the one that works without going into the grub menu (no longer dual booting on 1 drive).I assume you want to boot the third option on the menu. To do that you can either delete the first two, or where it says " default        0" change that to " default 2". That should fix it.

---

### Post by mikewhatever on 2007-11-10
So, which of the options does work? By the way, that has nothing to do with the MBR.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Bachstelze on 2007-11-10
> **asjdfwejqrfjcvm msz34rq33 said:**
> I assume you want to boot the third option on the menu. To do that you can either delete the first two, or where it says " default        0" change that to " default        4". That should fix it.

To boot the third option, it would be "default 2" ;)

---

### Post by Nano Geek on 2007-11-10
> **HymnToLife said:**
> To boot the third option, it would be "default 2" ;)Oh right, thanks.

---

### Post by svtfmook on 2007-11-10
awesome, that works.  thanks!

now, is there a way to have an option to boot to a windows installation on a separate RAID setup?

---

