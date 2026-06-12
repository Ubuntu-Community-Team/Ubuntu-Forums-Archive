---
title: "Grub - Error 13"
date: 2008-06-13
forum: General Help
---

### Post by OA-5599 on 2008-06-13
After i reinstalled ubuntu when I try to launch windows in the Grub boot loader it says:
"Error 13: Invalid or unsupported executable format"

When I first tried to launch ubuntu it also gave an error but I changed th line "root (hd0,0)" to "root (hd1,0) and now I can boot to ubuntu.

I tried changing this line for windows in different combination but nothing works...

---

### Post by OA-5599 on 2008-06-14
anyone:confused:

---

### Post by rraj.be on 2008-06-14
could you post the output.

something like'


```
Booting Microsoft Windows
root hd0,0
File system type is ext2fs, partition type 0x83
savedefault
make active
chainloader +1

Error 13
Invalid or unsupported executable format
```

but some thing may vary for you.

just post what you are getting while booting.

---

### Post by OA-5599 on 2008-06-16
Its just:

Error 13: Invalid or unsupported executable format

---

### Post by danwood76 on 2008-06-16
He means your menu.lst file.

So in terminal:
```

cat /boot/grub/menu.lst

```

---

### Post by OA-5599 on 2008-06-17
ok.

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
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
# kopt=root=UUID=ed80c262-e7da-4567-9e53-a8c37f11ad64 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title		Ubuntu 8.04, kernel 2.6.24-18-rt
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-rt root=UUID=ed80c262-e7da-4567-9e53-a8c37f11ad64 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-rt
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-rt (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-rt root=UUID=ed80c262-e7da-4567-9e53-a8c37f11ad64 ro single
initrd		/boot/initrd.img-2.6.24-18-rt

title		Ubuntu 8.04, kernel 2.6.24-16-rt
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-rt root=UUID=ed80c262-e7da-4567-9e53-a8c37f11ad64 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-rt
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-rt (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-rt root=UUID=ed80c262-e7da-4567-9e53-a8c37f11ad64 ro single
initrd		/boot/initrd.img-2.6.24-16-rt

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
# on /dev/sdb1
title		Windows XP Professional x64 Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

---

### Post by OA-5599 on 2008-06-17
I see that its for windows and ubuntu both "hd(1,0)"
But I don't know to what I should change it.

---

### Post by rraj.be on 2008-06-17
Post the out put of

```
sudo fdisk -l
```

---

### Post by OA-5599 on 2008-06-17
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd10b311d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096    7  HPFS/NTFS
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc457b704

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6994    56179273+  83  Linux
/dev/sdb2            6995        7297     2433847+   5  Extended
/dev/sdb5            6995        7297     2433816   82  Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x00b2dbff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      484518   244197040+  83  Linux

```

---

### Post by rraj.be on 2008-06-17
change root (hd1,0)
in windows to 

```
root (hd0,0)

```


That is change it here

```
title		Windows XP Professional x64 Edition
root		(hd1,0)
savedefault

```

Before that just make a copy of your menu.lst as backup for a safety measure.

---

### Post by OA-5599 on 2008-06-17
I tried that before but it just says "starting up..." and gets stuck there.

---

### Post by rraj.be on 2008-06-17
Is your windows starting or not.

Could you be a bit clear.

What happens actually when you boot windows from GRUB.

---

### Post by danwood76 on 2008-06-17
The problem you have is that the grub drive mapping is dependant on which drive you boot from.

Which drive is set to boot from in your BIOS?

---

### Post by rraj.be on 2008-06-17
Yup.

Danwood might be right.

Just try  changing your hard disk boot priority.

Further during posting your problem try to provide as much information as possible.
Thus every one can help you easily.

---

### Post by danwood76 on 2008-06-17
Im not saying change the boot priority as this will most likely cause more issues.
I'm simply inquiring as to which drive you are booting off, Im assuming its drive 0 (sda).
And so the map command would not be needed in grub.

I would change the windows entry to be this:
```

title		Windows XP Professional x64 Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```
This is just a guess on the info provided.

---

### Post by OA-5599 on 2008-06-17
I changed the boot priority in BIOS and now everything works.
Thank you all for your help!

---

