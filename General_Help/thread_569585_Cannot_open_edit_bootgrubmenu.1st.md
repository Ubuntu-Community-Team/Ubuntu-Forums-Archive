---
title: "Cannot open edit boot/grub/menu.1st"
date: 2007-10-07
forum: General Help
---

### Post by keithk50 on 2007-10-07
I need to edit my boot/grub/menu.1st but after numerous attempts it fails to open.   This message appears in Terminal:

gksudo gedit /boot/grub/menu.lst
(gedit:6328) GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

The file box opens but fails to display any information before 'greying out'.   I then have to force quit.  

Any help would be appreciated.    Thanks

---

### Post by tarunkool on 2007-10-07
try out this command in terminal

sudo gedit /boot/grub/manu.lst

---

### Post by tarunkool on 2007-10-07
sorry for wrong post

it is 

sudo gedit /boot/grub/menu.lst

---

### Post by keithk50 on 2007-10-07
Thanks for reply.   Here is what I got:

keith@keith-laptop:~$ sudo gedit /boot/grub/menu.lst
Password:
keith@keith-laptop:~$ 

Obviously I entered my Password!    Thanks again.

---

### Post by sandysandy on 2007-10-07
can u please tell me how to open grub editor. thanx.

---

### Post by kellemes on 2007-10-07
> **tarunkool said:**
> sorry for wrong post

it is 

sudo gedit /boot/grub/menu.lst

It should be "gksu gedit /boot/grub/menu.lst"

---

### Post by sandysandy on 2007-10-07
thanx for ur prompt help. i have opened the grub editor.
i have loaded 7.04 on my HDD but cannot boot from hdd. i am presently booted from live ubuntu 7.04 CD.
i have 2 hdd. first is 160 gb with windows on which one partition has ubuntu 7.04.
second HDD is 40 gb which  has only ubuntu 7.04.
but i am unable to boot either XP or 7.04.

will appreciate if u can tell me if any change has to be done with grub editor.

Thanx.

---

### Post by kellemes on 2007-10-07
Can you post menu.lst please?

---

### Post by sandysandy on 2007-10-07
the menu.lst is empty. there is nothing in it.

---

### Post by sandysandy on 2007-10-07
sorry. the menu.lst has the following entries ( quite long actually)

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
# kopt=root=UUID=254e52d1-f0f8-4f7c-ad23-e2c412bb280b ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=254e52d1-f0f8-4f7c-ad23-e2c412bb280b ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=254e52d1-f0f8-4f7c-ad23-e2c412bb280b ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by keithk50 on 2007-10-07
My post was 'hi-jacked'.   Can anyone help with my 'original' problem?.   I just can not get access to the grub menu.1st.    Thanks

---

### Post by nawitus on 2007-10-07
It is MENU.LST, not MENU.1ST. Obviously they're all lowercase.
Type 
```
sudo nano /boot/grub/menu.lst
```
 You need to know how to edit it though, type 
```
man update-grub
```

**sandysandy:**, please type
```

sudo fdisk -l

```
In terminal and reply what you get.

Also, type
```

nano /etc/fstab

```
and reply the contents of that file.
(ctrl+x exits the program)

---

### Post by sandysandy on 2007-10-08
[COLOR="Red"]with sudo fdisk -l the following displayed:-[/COLOR]

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2361    18964701   83  Linux
/dev/sda2            4559        4865     2465977+   5  Extended
/dev/sda3   *        2362        4558    17647402+  83  Linux
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris
/dev/sda6            4559        4660      819252   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3187    25599546    7  HPFS/NTFS
/dev/sdb2            3188       16581   107587305    f  W95 Ext'd (LBA)
/dev/sdb3   *       16582       19457    23101470   83  Linux
/dev/sdb5            3188        8286    40957686    7  HPFS/NTFS
/dev/sdb6            8287       13385    40957686    7  HPFS/NTFS
/dev/sdb7           13386       16451    24627613+   7  HPFS/NTFS
/dev/sdb8           16452       16581     1044193+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by sandysandy on 2007-10-08
[COLOR="Red"]with code nano /etc/fstab the following displayed[/COLOR]

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
/dev/sda6 swap swap defaults 0 0
/dev/sdb8 swap swap defaults 0 0

thanx

---

### Post by nawitus on 2007-10-08
sandysandy, that's a real mess. You're supposed to have only one swap (a size of your ram), and then one or more large ext3 partitions. NTFS is used by Windows. You should refer to this url for more information.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Boot_Menu](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Boot_Menu)

---

