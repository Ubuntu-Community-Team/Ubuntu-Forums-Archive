---
title: "[SOLVED] I've been silly and broken GRUB"
date: 2008-06-15
forum: General Help
---

### Post by Maelgwyn on 2008-06-15
Hi guys,

I have a dual-boot setup, where I have WinXP on a 40Gb drive, a 244Gb "media" partition and a 55.5Gb Ubuntu partition (the last 2 are on the same drive).

XP was playing up a lot, so I re-installed it but in the process I obviously wiped GRUB.
I've had a lot of help from a mate on MSN with this, but when Ubuntu updated and re-wrote menu.lst I'm back to square one!

Here's the output of fdisk -l
```

 ubuntu@ubuntu:/media/disk/boot/grub$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x57a77e9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       31871   256003776    7  HPFS/NTFS
/dev/sda2           31872       38620    54211342+  83  Linux
/dev/sda3           38621       38913     2353522+   5  Extended
/dev/sda5           38621       38913     2353491   82  Linux swap / Solaris

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008475a

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4864    39070048+   7  HPFS/NTFS

```

sudo grub -> find /boot/grub/stage1 gives me (hd1,1).

Please help a continual noob! :)

---

### Post by Pjotr123 on 2008-06-15
Check this:
[http://ubuntutip.googlepages.com/grub](http://ubuntutip.googlepages.com/grub)

---

### Post by Maelgwyn on 2008-06-15
Didn't help... I've used root (hd1,1) and it seemed to be fine, but when I reboot and get GRUB, I get told Error 22.
If I try to access WinXP through GRUB, I get told NTLDR is missing.
I tried root (hd0,1) but apparently that partition doesn't exist.

At the moment, if I want to access Ubuntu, I have to use the LiveCD, and if I want to access WinXP, I have to use my fix NTLDR CD. Windows seems to be the easiest as I can take the CD out once I've booted into Windows...

Please help!

---

### Post by Maelgwyn on 2008-06-15
if it's of any help, here's the output of sudo blkid:

```

ubuntu@ubuntu:~$ sudo blkid
/dev/hda1: UUID="2C3CE1E83CE1ACD0" TYPE="ntfs" 
/dev/sda1: UUID="3A00ADBB00AD7F0F" LABEL="Media" TYPE="ntfs" 
/dev/sda2: UUID="d16f5116-b5fc-4546-bbe2-7c2a775af069" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="15b0fe19-4f9f-400e-92cc-cd49eb334b69" TYPE="swap" 
/dev/loop0: TYPE="squashfs"

```

I'm going to try SuperGRUB CD now. Wish me luck!

---

### Post by Maelgwyn on 2008-06-15
OK.

Using SuperGRUB, I've determined the following:

(hd0) = Windows XP (theoretically also the location of MBR?)
(hd1) = (hd1,0) - NTFS = This must be my 'Media' partition
            (hd1,1) - Ubuntu 8.04
            (hd1,4) - swap.

So I booted the MBR using SuperGRUB, from (hd0), and selected Ubuntu. It worked!

What do I need to type into the grub> prompt to update everything accordingly?

---

### Post by logos34 on 2008-06-15
> grub> find /boot/grub/stage1
(should output 'hd1,1')

grub> root (hd1,1)

grub> setup (hd0)

grub> quit

should work, but that's apparently what you already did.

try it again.  maybe you'll get lucky this time.

That still leaves the problem of windows not booting.

ADD:
make sure /boot/grub/menu.lst still reads (hd1,1) for ubuntu entries.  It shouldn't have changed.

---

### Post by Maelgwyn on 2008-06-15
Oddly enough, now that I'm actually *in* my Ubuntu partition, rather than running off the LiveCD, grub> gives me (hd0,1) as my /stage1...

Does this mean that #groot should be (hd0,1)?
and the kernel options in menu.lst should be (1,1)?

Here's menu.lst...

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=d16f5116-b5fc-4546-bbe2-7c2a775af069 ro

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

title        Ubuntu 8.04, kernel 2.6.24-19-generic
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=d16f5116-b5fc-4546-bbe2-7c2a775af069 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=d16f5116-b5fc-4546-bbe2-7c2a775af069 ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04, kernel 2.6.24-17-generic
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-17-generic root=UUID=d16f5116-b5fc-4546-bbe2-7c2a775af069 ro quiet splash
initrd        /boot/initrd.img-2.6.24-17-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-17-generic root=UUID=d16f5116-b5fc-4546-bbe2-7c2a775af069 ro single
initrd        /boot/initrd.img-2.6.24-17-generic

title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=d16f5116-b5fc-4546-bbe2-7c2a775af069 ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=d16f5116-b5fc-4546-bbe2-7c2a775af069 ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04, kernel 2.6.24-15-generic
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-15-generic root=UUID=d16f5116-b5fc-4546-bbe2-7c2a775af069 ro quiet splash
initrd        /boot/initrd.img-2.6.24-15-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-15-generic (recovery mode)
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-15-generic root=UUID=d16f5116-b5fc-4546-bbe2-7c2a775af069 ro single
initrd        /boot/initrd.img-2.6.24-15-generic

title        Ubuntu 8.04, kernel 2.6.24-14-generic
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-14-generic root=UUID=d16f5116-b5fc-4546-bbe2-7c2a775af069 ro quiet splash
initrd        /boot/initrd.img-2.6.24-14-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-14-generic (recovery mode)
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-14-generic root=UUID=d16f5116-b5fc-4546-bbe2-7c2a775af069 ro single
initrd        /boot/initrd.img-2.6.24-14-generic

title        Ubuntu 8.04, kernel 2.6.24-12-generic
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-12-generic root=UUID=d16f5116-b5fc-4546-bbe2-7c2a775af069 ro quiet splash
initrd        /boot/initrd.img-2.6.24-12-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-12-generic (recovery mode)
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-12-generic root=UUID=d16f5116-b5fc-4546-bbe2-7c2a775af069 ro single
initrd        /boot/initrd.img-2.6.24-12-generic

title        Ubuntu 8.04, kernel 2.6.24-11-generic
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-11-generic root=UUID=d16f5116-b5fc-4546-bbe2-7c2a775af069 ro quiet splash
initrd        /boot/initrd.img-2.6.24-11-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-11-generic (recovery mode)
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-11-generic root=UUID=d16f5116-b5fc-4546-bbe2-7c2a775af069 ro single
initrd        /boot/initrd.img-2.6.24-11-generic

title        Ubuntu 8.04, memtest86+
root        (hd1,1)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1

```

---

### Post by logos34 on 2008-06-15
> **Maelgwyn said:**
> Oddly enough, now that I'm actually *in* my Ubuntu partition, rather than running off the LiveCD, grub> gives me (hd0,1) as my /stage1...

Does this mean that #groot should be (hd0,1)?
and the kernel options in menu.lst should be (1,1)?


hmmm...maybe when you changed the device boot order in the bios to boot frm the cdrom it threw off the hard disk order.  Might check it.  Also check /boot/grub/device.map. It should be consistent with menu.lst.

groot and root should be the same (it's only different if you have, say, a separate /boot).

I'd just go with what it reports, root as '(hd0,1)', and setup (hd1).  Then reboot to hda.  See if that works

---

### Post by unutbu on 2008-06-15
Use this post to determine the mapping between GRUB notation for partitions (hd x,y) and device names for partitions /dev/sd**: 
[http://ubuntuforums.org/showpost.php?p=5114814&postcount=378](http://ubuntuforums.org/showpost.php?p=5114814&postcount=378)

> (hd0) = Windows XP (theoretically also the location of MBR?)
(hd1) = (hd1,0) - NTFS = This must be my 'Media' partition
(hd1,1) - Ubuntu 8.04
(hd1,4) - swap.
hd0 and hd1 refer to entire drives. (hd x,y) refer to partitions.

groot is used by update-grub, not GRUB per se. It won't make a difference what you set it to at this stage.

device.map too is not used by GRUB at boot time. It is read by GRUB when you run the 'setup' command, but we won't know if you need to edit it until we straighten out what the mapping between (hd x,y) and partitions is according to GRUB.

---

### Post by logos34 on 2008-06-15
Maybe he just got a little sloppy, becuse it's clear to me he meant

> (hd0**,0**) = Windows XP (theoretically also the location of MBR?)
(hd1,0) - NTFS = This must be my 'Media' partition
(hd1,1) - Ubuntu 8.04
(hd1,4) - swap.

---

### Post by Maelgwyn on 2008-06-15
> **logos34 said:**
> Maybe he just got a little sloppy, becuse it's clear to me he meant

lol yes. Sorry!

---

### Post by unutbu on 2008-06-15
Ok, my bad! :)

---

### Post by meierfra. on 2008-06-15
deleted

---

### Post by Maelgwyn on 2008-06-15
alright, thanks for that :)

I've updated menu.lst but still getting the same error... 22 for Ubuntu, no NTLDR for WinXP.
If I run off SuperGRUB though, I don't have any issues...

here's menu.lst again
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=d16f5116-b5fc-4546-bbe2-7c2a775af069 ro

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
# howmany=3

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

title        Ubuntu 8.04, kernel 2.6.24-19-generic
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=d16f5116-b5fc-4546-bbe2-7c2a775af069 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=d16f5116-b5fc-4546-bbe2-7c2a775af069 ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04, kernel 2.6.24-17-generic
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-17-generic root=UUID=d16f5116-b5fc-4546-bbe2-7c2a775af069 ro quiet splash
initrd        /boot/initrd.img-2.6.24-17-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-17-generic root=UUID=d16f5116-b5fc-4546-bbe2-7c2a775af069 ro single
initrd        /boot/initrd.img-2.6.24-17-generic

title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=d16f5116-b5fc-4546-bbe2-7c2a775af069 ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=d16f5116-b5fc-4546-bbe2-7c2a775af069 ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04, kernel 2.6.24-15-generic
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-15-generic root=UUID=d16f5116-b5fc-4546-bbe2-7c2a775af069 ro quiet splash
initrd        /boot/initrd.img-2.6.24-15-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-15-generic (recovery mode)
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-15-generic root=UUID=d16f5116-b5fc-4546-bbe2-7c2a775af069 ro single
initrd        /boot/initrd.img-2.6.24-15-generic

title        Ubuntu 8.04, kernel 2.6.24-14-generic
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-14-generic root=UUID=d16f5116-b5fc-4546-bbe2-7c2a775af069 ro quiet splash
initrd        /boot/initrd.img-2.6.24-14-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-14-generic (recovery mode)
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-14-generic root=UUID=d16f5116-b5fc-4546-bbe2-7c2a775af069 ro single
initrd        /boot/initrd.img-2.6.24-14-generic

title        Ubuntu 8.04, kernel 2.6.24-12-generic
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-12-generic root=UUID=d16f5116-b5fc-4546-bbe2-7c2a775af069 ro quiet splash
initrd        /boot/initrd.img-2.6.24-12-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-12-generic (recovery mode)
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-12-generic root=UUID=d16f5116-b5fc-4546-bbe2-7c2a775af069 ro single
initrd        /boot/initrd.img-2.6.24-12-generic

title        Ubuntu 8.04, kernel 2.6.24-11-generic
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-11-generic root=UUID=d16f5116-b5fc-4546-bbe2-7c2a775af069 ro quiet splash
initrd        /boot/initrd.img-2.6.24-11-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-11-generic (recovery mode)
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-11-generic root=UUID=d16f5116-b5fc-4546-bbe2-7c2a775af069 ro single
initrd        /boot/initrd.img-2.6.24-11-generic

title        Ubuntu 8.04, memtest86+
root        (hd1,1)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


```

---

### Post by meierfra. on 2008-06-15
Try this

At the grub menu at boot up, select Ubuntu, but do not press enter.Press "e" instead. At the new screen press "e" again. 

Change "root (hd1,1)" to root "(hd0,1)"

Press "enter" and then "b" to boot.

This should boot you into ubuntu.
Once you booted into Ubuntu, you still need to make this change permanent:

Open a terminal and type

```
sudo update-grub
gksudo gedit /boot/grub/menu.lst
```


Change the Windows Item to

title        Microsoft Windows XP Professional
root        (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader    +1

Save the file. And hopefully all your problems are fixed.

---

### Post by Maelgwyn on 2008-06-15
by joves, it works! *huzzah*!

---

### Post by logos34 on 2008-06-15
so it looks like all that happened was your boot drive got switched, although how that happened is odd since, if anything, it should have remained the windows drive, especially after reinstalling it. 

Since you're now booting off sda, you could even restore XP bootloader to the MBR of hda to allow you direct access in case you ever have another problem with linux.

---

