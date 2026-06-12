---
title: "[SOLVED] GRUB disaster"
date: 2008-01-30
forum: General Help
---

### Post by tstack77 on 2008-01-30
I have Gutsy and XP installed on the same SATA drive. I installed an old PATA drive to use as a back up and when I reset my pc it defaulted to the IDE drive as the master. I went into the bios and changed it back to boot from the SATA, but when I did GRUB was screwed. 

Using the liveCD I fixed GRUB in the terminal using the same method I used after installing XP (below).

grub> find /boot/grub/stage1

grub> root (hd0,1) #Hit the <Enter> key

grub> setup (hd0) #Hit <Enter> key

grub> quit #Hit <Enter> key, quits grub

After rebooting I was able to see the GRUB options but neither worked. I then decided to give Super GRUB Disc a try. After selecting the automatic fix option and told that everything was a success, I still get these errors:

In Gutsy:
Error 17: Cannot mount selected Partition

In XP:
Starting up...
Non-System disk
Press any key to reboot

What's my next step? :confused:

Side: I am able to directly boot into XP and Gutsy using the SGD

---

### Post by Fixman on 2008-01-30
cat /boot/grub/menu.lst and post the results, maybe? Oh, and does XP work?

---

### Post by jwmislan on 2008-01-30
Looks like you should boot up with the ubuntu gutsy cd and choose live cd boot 
option.

Then when you are logged in, check all your drives to see where they are mounting at.

You should then as well, be able to get on the net to get more help from the forum folks here.

We need your disk stats - like,  cat /proc/mounts

good luck
JohnWM

---

### Post by tstack77 on 2008-01-30
I just got home to try and fix this and am now in the liveCD. I tried SGD to get in but can no longer boot into Gutsy (now error 21). However, I am still able to boot directly into XP using the disk.

jwmislan, here are the results of cat /proc/mounts:

ubuntu@ubuntu:~$ cat /proc/mounts
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
/dev/scd0 /cdrom iso9660 ro,noatime 0 0
/dev/loop0 /rofs squashfs ro,noatime 0 0
tmpfs /cow tmpfs rw,noatime 0 0
unionfs / unionfs rw,noatime,dirs=/cow=rw:/rofs=ro,debug=4294967295,delete=whiteout 0 0
unionfs /dev/.static/dev unionfs rw,noatime,dirs=/cow=rw:/rofs=ro,debug=4294967295,delete=whiteout 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
tmpfs /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
/dev/sda1 /media/disk fuseblk rw,nosuid,nodev,noatime,user_id=0,group_id=0,allow_other 0 0
/dev/sda2 /media/disk-1 ext3 rw,nosuid,nodev,data=ordered 0 0

Fixman, here is the complete /boot/grub/menu.lst:

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
timeout		2

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
# kopt=root=UUID=9cf828c5-63b7-471b-bb42-13b929a0c8ca ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9cf828c5-63b7-471b-bb42-13b929a0c8ca ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9cf828c5-63b7-471b-bb42-13b929a0c8ca ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by logos34 on 2008-01-30
Turn off the pc.  Disconnect the IDE drive (just pull 4-pin molex power plug).

Boot the Live cd.  Mount root partition (double-click on it in Places>computer) and edit menu.lst:

**gksudo gedit /media/disk/boot/grub/menu.lst** (it usually mounts at '/media/disk')

Change 'groot' and ubuntu 'root' lines to **(hd[COLOR="Red"]0[/COLOR],1)**.

Change windows to **(hd[COLOR="Red"]0[/COLOR],0)**.  Remove the 'map' commands.

Now[ reinstall grub to the mbr]("http://ubuntuforums.org/showthread.php?t=224351").

Reconnect up the IDE but make sure the Bios hard disk boot order still lists the sata first.

---

### Post by tstack77 on 2008-01-30
You my friend, are AWESOME!

It all makes sense now and works perfectly. Thank you!

---

### Post by logos34 on 2008-01-30
Ok.  Glad to help!

Mark as 'solved' (>thread tools)

enjoy

---

### Post by Shazaam on 2008-01-30
Be carefull doing a kernel update as this may re-write grub and will probably generate the same errors. Make sure you print logos34's instructions for later use.
The reason I say this is because during my uber-noob period with Ubuntu Dapper I did some tweaking that only testdisk was able to fix. :)

---

