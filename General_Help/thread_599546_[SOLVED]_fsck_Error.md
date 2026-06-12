---
title: "[SOLVED] fsck Error"
date: 2007-11-01
forum: General Help
---

### Post by kshane on 2007-11-01
I'm hoping there's a simple fix for this...

I installed a new Linux OS this morning:  StartCom.  It's supposed to be really great for doing multimedia stuff.  Well, first, when I rebooted, there was no option for Ubuntu, so I used Super Grub and fixed it so that Ubuntu would boot.  Then I couldn't boot to StartCom, so I went to the grub menu that it wrote and copied the entry for StartCom and put it in the Ubuntu grub menu.lst.  Now they both boot, but I get an fsck error each time I boot to Ubuntu.  I looked at the log file it wrote and I am lost.  The entry is below:

```

Log of fsck -C -R -A -a 
Thu Nov  1 09:28:03 2007

fsck 1.40.2 (12-Jul-2007)
/dev/sda4: clean, 2551/6979584 files, 5538669/13952452 blocks (check in 4 mounts)
fsck.ext3: Unable to resolve 'UUID=278672a9-9db7-40db-96f4-9691b3874fa4'

fsck died with exit status 8

Thu Nov  1 09:28:04 2007
----------------

```

The referenced partition is the one I installed StartCom on.  It's not a new partition, I just hadn't been using it.  Below is my fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=c1dd7906-ecf3-403c-8348-9701b828e691 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=7198D00F73629629 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=5e70c11b-d4a5-4cd6-9c1a-4a81e11ecffe /media/sda4     ext3    defaults        0       2
# /dev/sda5
UUID=278672a9-9db7-40db-96f4-9691b3874fa4 /media/sda5     ext3    defaults        0       2
# /dev/sda6
UUID=ebf9e319-ccac-4b71-b585-88c0cea88134 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

The only REAL problem now is that when booting to Ubuntu the login screen doesn't come up.  I get a grub command line.  If I exit it, them the Gnome login screen comes up and everything is pretty much fine, except that Ubuntu seems a little "jerky", like it's hesitating a split second before executing any commands.  That I guess I can figure out and smooth over on my own.  I would just like to clean up the error that's stopping a smooth transition from cold boot to login.

Any ideas, folks?   :confused:

Thanks in advance!  

Kevin

---

### Post by kshane on 2007-11-01
<bump>

Any one?   :)

---

### Post by bingoUV on 2007-11-01
Do you use StartCom partition when you are in ubuntu? If you don't use it, or use it very rarely, you can prevent its fsck when booting ubuntu. In your fstab, replace the StartCom partition line by
```

UUID=278672a9-9db7-40db-96f4-9691b3874fa4 /media/sda5     ext3    defaults        0       2

```

This is not a solution, but a workaround. This should be reasonable if you do not use StartCom partition much in ubuntu, and any way when you boot StartCom, the partition will be fscked, so not much risk.

There could be a problem with your grub.conf also, please post that too. That might be the real reason of login screen not coming up.

---

### Post by kshane on 2007-11-01
> **bingoUV said:**
> Do you use StartCom partition when you are in ubuntu? If you don't use it, or use it very rarely, you can prevent its fsck when booting ubuntu. In your fstab, replace the StartCom partition line by
```

UUID=278672a9-9db7-40db-96f4-9691b3874fa4 /media/sda5     ext3    defaults        0       2

```

This is not a solution, but a workaround. This should be reasonable if you do not use StartCom partition much in ubuntu, and any way when you boot StartCom, the partition will be fscked, so not much risk.

There could be a problem with your grub.conf also, please post that too. That might be the real reason of login screen not coming up.

I don't use StartCom's partition at all from Ubuntu.  The code line you posted is the same as the one already there.  Did you mean I should remove it?

There is no grub.conf in Ubuntu.  Did a file search and nothing came up.  It's not in /boot or /boot/grub.  I DO have a file by that name in StartCom under /boot/grub/grub.conf.  That file has nothing in it.

**And thanks for reading this..  I REALLY appreciate it.**

Kevin

---

### Post by bingoUV on 2007-11-01
Really sorry, I meant to edit it just a little bit. Instead of the last 2, make it 0
```

UUID=278672a9-9db7-40db-96f4-9691b3874fa4 /media/sda5     ext3    defaults        0       0

```

---

### Post by bingoUV on 2007-11-01
and instead of grub.conf, give us this file : /boot/grub/menu.lst

---

### Post by kshane on 2007-11-01
> **bingoUV said:**
> and instead of grub.conf, give us this file : /boot/grub/menu.lst

I just made the change you suggested and rebooted.  I no longer get the error - it boots right to the login screen.

But, since this isn't the actual fix, but a workaround, here's the Ubuntu menu.lst:
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
timeout		30

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
# kopt=root=UUID=c1dd7906-ecf3-403c-8348-9701b828e691 ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c1dd7906-ecf3-403c-8348-9701b828e691 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title 		StartCom MultiMedia Edition (2.6.16-1.ML5.2)
root		(hd0,4)
kernel 		/boot/vmlinuz-2.6.16-1.ML5.2 ro root=LABEL=/ rhgb quiet
initrd 		/boot/initrd-2.6.16-1.ML5.2.img


title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c1dd7906-ecf3-403c-8348-9701b828e691 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

Again, many thanks...

Kevin

---

### Post by bingoUV on 2007-11-01
This seems to be depending upon the label of /dev/sda5 to be /. Install gparted, and run it as  root to see whether the label of this partition is really / (see under the label column). Also, can you post the output of the following command :
```

ls -l  /dev/disk/by-uuid/

```

---

### Post by kshane on 2007-11-01
> **bingoUV said:**
> This seems to be depending upon the label of /dev/sda5 to be /. Install gparted, and run it as  root to see whether the label of this partition is really / (see under the label column). Also, can you post the output of the following command :
```

ls -l  /dev/disk/by-uuid/

```

From Gparted:
```

/dev/sda5

```

And...
```

kevin@enigma:~$ ls -l  /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2007-11-01 04:02 5e70c11b-d4a5-4cd6-9c1a-4a81e11ecffe -> ../../sda4
lrwxrwxrwx 1 root root 10 2007-11-01 11:31 7198D00F73629629 -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-11-01 11:31 ad61baa8-f54a-449f-be12-0106a38cac03 -> ../../sda5
lrwxrwxrwx 1 root root 10 2007-11-01 04:02 c1dd7906-ecf3-403c-8348-9701b828e691 -> ../../sda2
lrwxrwxrwx 1 root root 10 2007-11-01 04:02 ebf9e319-ccac-4b71-b585-88c0cea88134 -> ../../sda6

```

Kevin

---

### Post by bingoUV on 2007-11-01
I did not understand what gparted said. Was the space under the label column empty in gparted? 

The UUID given in the fstab is wrong. Try changing it to 
```

UUID=ad61baa8-f54a-449f-be12-0106a38cac03  /media/sda5     ext3    defaults        0       2

```
Now you can put the last digit as 2 in the fstab entry. There should be no error even if ubuntu fsck's SmartCom's partition.

---

### Post by kshane on 2007-11-01
> **bingoUV said:**
> I did not understand what gparted said. Was the space under the label column empty in gparted? 

The UUID given in the fstab is wrong. Try changing it to 
```

UUID=ad61baa8-f54a-449f-be12-0106a38cac03  /media/sda5     ext3    defaults        0       2

```
Now you can put the last digit as 2 in the fstab entry. There should be no error even if ubuntu fsck's SmartCom's partition.

***That did the trick!  Perfect!  I can't thank you enough..***.  I was getting stressed thinking no one would get involved with this one...  :)

I've only been using Linux/Ubuntu since the end of May, this year.  It's been one helluva learning curve.  But, people like you are what got me through!  *You're a Godsend!*

Now to "tweak" StartCom...  It's not working too great, but it's a fresh install, sooooo...

Thanks Again!

Kevin

---

