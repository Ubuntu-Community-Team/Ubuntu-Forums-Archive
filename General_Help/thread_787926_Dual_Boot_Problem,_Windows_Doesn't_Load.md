---
title: "Dual Boot Problem, Windows Doesn't Load"
date: 2008-05-09
forum: General Help
---

### Post by ForksHolder on 2008-05-09
Hello.
On my nc6220 compaq laptop, i have a dual boot between ubuntu and windows xp.

In the boot mentu, when i choose windows it writes "error" very fast and turns back again to the menu.

i have no idea why could it happend... any ideas?

Thanks,
Holder.

---

### Post by hermes0710 on 2008-05-09
Can you post the contents of /boot/grub/menu.lst and /etc/fstab?

---

### Post by logos34 on 2008-05-09
did you change ANY settings recently in either OS?  

Try Super Grub Disk to boot windows

---

### Post by ForksHolder on 2008-05-11
/boot/grub/menu.lst:

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=e78abf10-932f-4ca3-b457-ef0e3cb5c711 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e78abf10-932f-4ca3-b457-ef0e3cb5c711 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e78abf10-932f-4ca3-b457-ef0e3cb5c711 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
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
title		Microsoft Windows XP Professional (TuneUp Backup)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


/etc/fstab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=e78abf10-932f-4ca3-b457-ef0e3cb5c711 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=de87c46e-916c-4d76-8039-d2020a7dc843 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

About the changes,
Yes, I did try to get a SUSE grub by this thread:
[http://ubuntuforums.org/showthread.php?t=208855](http://ubuntuforums.org/showthread.php?t=208855)

It did warked but with the error...

If it's passibale, it's the best that 2 of the will work..

Thanks,
ForksHolder.

---

### Post by ghost_ryder35 on 2008-05-11
[quote=]
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda6
UUID=e78abf10-932f-4ca3-b457-ef0e3cb5c711 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=de87c46e-916c-4d76-8039-d2020a7dc843 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0 
[/quote]
is that everything in your fstab??  if it is your missing some things like sda0 through sda4 (well it might skip one or two for logical instead of primary)

---

### Post by ForksHolder on 2008-05-11
Well.. Can you tell me exacully what to write?

---

### Post by ForksHolder on 2008-05-11
Mistake

---

### Post by logos34 on 2008-05-11
Post 

sudo fdisk -l

Some things you could try:

sudo cfdisk

-flag sda1 (windows) 'bootable' if it isn't already

-mark windows for disk check next boot.  You can do it from linux:

sudo apt-get install ntfsprogs

sudo ntfsfix

then try to reboot into windows

-Or you could try booting from windows install cd and run **fixboot**

---

### Post by ForksHolder on 2008-05-17
> holder@holder-laptop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac3bac3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4227    33951928+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            4228        9729    44194815    f  W95 Ext'd (LBA)
/dev/sda5            4228        4419     1542208+  82  Linux swap / Solaris
/dev/sda6            4420        9729    42652543+  83  Linux



I've tried everything you said =\ still the same error..

---

### Post by logos34 on 2008-05-17
The next thing I'd try is [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk"). If possible, mount windows in linux, backup your files.  Linux files too. 

Be careful and good luck

---

