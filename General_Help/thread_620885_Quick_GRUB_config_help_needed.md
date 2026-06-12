---
title: "Quick GRUB config help needed"
date: 2007-11-23
forum: General Help
---

### Post by Hemmer on 2007-11-23
Hi I'm having difficulty configuring GRUB correctly. Here is the output of fdisk -l

```
sudo fdisk -l

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00021c38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13058   104887361    7  HPFS/NTFS
/dev/sda2           13059       17298    34057800   83  Linux
/dev/sda3           17299       24309    56315857+   7  HPFS/NTFS
/dev/sda4           24310       24792     3879697+   5  Extended
/dev/sda5           24310       24792     3879666   82  Linux swap / Solaris

```


relavent section of menu.lst
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

title		Windows Vista
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

title		Windows XP
rootnoverify	(hd0,2)
makeactive
chainloader	+1

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
# kopt=root=UUID=521d6c05-4fe4-4d69-b20b-4726bcbdff93 ro

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
# defoptions=quiet splash vga=791

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

splashimage=(hd0,1)/boot/grub/blue.xpm.gz

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=521d6c05-4fe4-4d69-b20b-4726bcbdff93 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=521d6c05-4fe4-4d69-b20b-4726bcbdff93 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=521d6c05-4fe4-4d69-b20b-4726bcbdff93 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=521d6c05-4fe4-4d69-b20b-4726bcbdff93 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST





```

The ubuntu partition works fine, but there is some trouble getting XP and Vista to work.

sda1 is my 100gb vista installation (NTFS)
sda3 is my 50gb xp installation (NTFS)

When i choose the vista option, it loads XP (on sda3), and when i choose XP, it just hangs on a message saying:

```
Starting up...
```

Would really apprieciate any help with this, cheers Hemmer

---

### Post by Hemmer on 2007-11-23
bump

---

### Post by LaRoza on 2007-11-23
> **Hemmer said:**
> bump

I looked over the problem and found no answer, so I didn' respond so other members of the Unanswered Posts Team would find it.

You bumped it after an hour, you should have waited about 48 hours.

Post the entire menu.lst, so future posters don't have to ask, and I may see something...

---

### Post by Hemmer on 2007-11-23
I'm sorry. You're absolutely right. I've added the whole menu.lst to my first post.

The thing thats confusing me is why (hd0,0) boots the 50gb xp partion (and vis-versa)?

---

### Post by LaRoza on 2007-11-23
Try:
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
# kopt=root=UUID=521d6c05-4fe4-4d69-b20b-4726bcbdff93 ro

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
# defoptions=quiet splash vga=791

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

splashimage=(hd0,1)/boot/grub/blue.xpm.gz

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=521d6c05-4fe4-4d69-b20b-4726bcbdff93 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=521d6c05-4fe4-4d69-b20b-4726bcbdff93 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=521d6c05-4fe4-4d69-b20b-4726bcbdff93 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=521d6c05-4fe4-4d69-b20b-4726bcbdff93 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

title		Windows XP
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

title		Windows Vista Broke
rootnoverify	(hd0,2)
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST

```

(I moved the Windows entries to the end)

---

### Post by namanbagga on 2007-11-23
Try changing rootnoverify to root:popcorn:

---

### Post by Hemmer on 2007-11-23
> **namanbagga said:**
> Try changing rootnoverify to root:popcorn:

I had it like this originally, but that didn't work either. Also moving the Windows entry didn't help. I think im gonna just go for a fresh install of xp and keep ubuntu working. planning to ditch vista alltogether as it is slow and bloated on my computer anyways. Thanks for the suggestions guys, and sorry for bumping too soon. 

Hemmer

---

### Post by LaRoza on 2007-11-23
> **Hemmer said:**
> I had it like this originally, but that didn't work either. Also moving the Windows entry didn't help. I think im gonna just go for a fresh install of xp and keep ubuntu working. planning to ditch vista alltogether as it is slow and bloated on my computer anyways. Thanks for the suggestions guys, and sorry for bumping too soon. 

Hemmer

You could try a reinstall of Grub, it may fix it. Sorry, I can't see anything wrong.

---

### Post by ztomic on 2007-11-23
Same problem here.
Windows 2000 on (hd1)
Ubuntu on (hd0)

I added after ##End Automagic:
```
title Windows 2000
root (hd1,0)
makeactive
chainloader +1

```

I installed the new hard drive after ubuntu was already loaded. Disconnected the Ubuntu drive and installed 2000 on the new drive. Then I connected the Ubuntu drive on primary and the 2000 drive on secondary connectors. Did the above edit to /boot/grub/menu.lst. When I try to boot 2000 it stalls on "Starting..."

---

### Post by torgrot on 2007-11-23
In order to boot windows of a second hard drive you need to add the following lines to menu.lst 
map		(hd0) (hd1)
map		(hd1) (hd0)

Here is my entry for WinXP on a second hard drive hd1

title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

I didn't think you could boot Vista from grub.  I believe you need EasyBCD as your boot manager.

torgrot

---

### Post by ztomic on 2007-11-23
Yup that worked.
:)

---

