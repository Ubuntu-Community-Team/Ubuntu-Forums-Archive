---
title: "Add WinXP to grub config..."
date: 2007-06-19
forum: General Help
---

### Post by bronze on 2007-06-19
I installed Ubuntu first, onto the primary partition. Later I used an **image** to copy the file/folder structure for windows XP onto another NTFS partition. Now, I need to add this OS into the menu.lst of grub.

First, here's my current partition setup:

```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+  83  Linux
/dev/sda2           29645       30401     6080602+   5  Extended
/dev/sda3            3825       24221   163838902+  83  Linux
/dev/sda4           24222       29644    43560247+   7  HPFS/NTFS
/dev/sda5           29645       30401     6080571   82  Linux swap / Solaris

```

And here's the menu.lst as of now:

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
# kopt=root=UUID=b85e07a9-a0f3-4e5c-907f-1fa9369b5601 ro

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
# defoptions=quiet splash locale=nb_NO

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=b85e07a9-a0f3-4e5c-907f-1fa9369b5601 ro quiet splash locale=nb_NO
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=b85e07a9-a0f3-4e5c-907f-1fa9369b5601 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b85e07a9-a0f3-4e5c-907f-1fa9369b5601 ro quiet splash locale=nb_NO
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b85e07a9-a0f3-4e5c-907f-1fa9369b5601 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

What lines do I need to add? I want the setup to be like this:
Default OS: Ubuntu
Timeout: 10 seconds (before Ubuntu is automatic selected).
Secondary OS: Windows XP

**I would appreciate if you just pasted the code for a new menu.lst, to ensure that the needed lines are placed correctly!**

-bronze

---

### Post by cogadh on 2007-06-19
Not sure if this is still true, but Windows XP used to need to be installed first on the drive, then Ubuntu. Win doesn't play second banana well and won't boot if it is not the first OS on the drive.

Besides, if you do it that way, the Ubuntu install automatically makes itself the default OS and still adds Windows as an optional OS in GRUB.

---

### Post by confused57 on 2007-06-19
This entry "might" work:
```
title   Windows XP
root   (hd0,3)
savedefault
makeactive
chainloader +1
```

Just add the entry to the very end of your menu.lst.

---

### Post by bronze on 2007-06-20
> **confused57 said:**
> This entry "might" work:
```
title   Windows XP
root   (hd0,3)
savedefault
makeactive
chainloader +1
```

Just add the entry to the very end of your menu.lst.

This did not do it for me, but I might have done it wrong... Was it supposed to be before or after this:
```
### END DEBIAN AUTOMAGIC KERNELS LIST
```

Anyways, I tried it on both sides, and I still get no menu when I boot. Just "loading, stage 1,5, press esc to enter the menu".

Never really tried to press esc, but I don't think it matters. Still, I will try it now.

In the meantime, why don't anyone else come with a suggestion. I want to avoid re-installs of either OS, but if it's the last solution....

Edit: I rebooted, pressed esc and got a menu with different boot options, whereas "Windows XP" was a choice, but when I chose it, it didn't boot XP, so I'm thinking that this part might be wrong:
```
root   (hd0,3)
```

Any comments on this?

---

### Post by bronze on 2007-06-20
Please read the "edit" part of previous post.

After selecting windows xp in the grub boot-up menu, the fdisk -l has changed. Take a look:
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3824    30716248+  83  Linux
/dev/sda2           29645       30401     6080602+   5  Extended
/dev/sda3            3825       24221   163838902+  83  Linux
/dev/sda4   *       24222       29644    43560247+   7  HPFS/NTFS
/dev/sda5           29645       30401     6080571   82  Linux swap / Solaris

```

As you can see, sda4, or the NTFS Windows partition has now become "boot". Still, I can't boot into it.

---

### Post by confused57 on 2007-06-20
You can try rootnoverify, instead of root, and remove the savedefault line:
```
title   Windows XP
rootnoverify   (hd0,3)
makeactive
chainloader +1
```

I would also suggest burning a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
SGD "might" be able to boot your Window's partition.

---

