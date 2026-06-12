---
title: "'Catch 22' dual boot dilemma"
date: 2008-04-19
forum: General Help
---

### Post by foongkev on 2008-04-19
Hi guys,

I just stated using Ubuntu recently and I love it. I'm having a problem however and I'm having difficulty finding the solution form it online. Maybe I just don't know how to search for it properly.

Anyway, there was an error recently with my boot, and I solve it from editing the menu.lst file which contained root (hd1,3) to root (hd0,3) to boot Ubuntu. I don't know why it suddenly changed from the partition being on 'hd1' to 'hd0'. My real problem, however (I'm not sure if it is related to this problem I solved) might only be conincidental.

Ever since then when I try to boot up Vista it provided the screen:

```

Windows Boot Manager

Windows failed to start. A recent hardware or software change might be the cause....etc (I'm sure most people have seen this screen before, and then it goes:)

File: \Boot\BCD
Status: 0xc0000001
Info: An error occured while attempting to read the boot configuration data
```

So obviously I popped in me Vista disc, went to command prompt and typed 'bootrec /fixmbr' and 'bootrec /fixboot'

So when I boot up it instantly goes to the Vista bootup screen because I obviously overwrote GRUB with the Vista boot files.

What I did to solve that is boot up my pc with the Ubuntu disc to boot in live session mode, sudo into grub, and restore grub by typing the usual root (hd0,3) and setup (hd0), reboot and grub is working and I can boot into linux. However now in grub when I choose the option to boot Vista the initial Vista boot error comes up again!

So it seems like its an endless loop in a way, restoring Vista boot -> restore grub ->restore Vista boot.... etc.

In case it might help, here's my menu.lst file:

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
timeout		5

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
# kopt=root=UUID=06fcde22-6332-4260-bb69-93b66cb7f6cc ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,3)

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
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=06fcde22-6332-4260-bb69-93b66cb7f6cc ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=06fcde22-6332-4260-bb69-93b66cb7f6cc ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

and also my fdisk -l info:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
240 heads, 63 sectors/track, 64601 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xccc6ec48

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         555     4195768+   7  HPFS/NTFS
/dev/sda2             556       62975   471895200    f  W95 Ext'd (LBA)
/dev/sda3           62976       63104      975240   82  Linux swap / Solaris
/dev/sda4           63105       64601    11317320   83  Linux
/dev/sda5             556        5973    40960048+   7  HPFS/NTFS
/dev/sda6            5974        8005    15361888+   7  HPFS/NTFS
/dev/sda7            8006       57827   376654288+   7  HPFS/NTFS
/dev/sda8           57828       62975    38915848+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b900b90

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         523     4194304    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2             523       13271   102400000    7  HPFS/NTFS
/dev/sdb3           13271       53153   320348160    7  HPFS/NTFS
/dev/sdb4           53153       60801    61440000    f  W95 Ext'd (LBA)
/dev/sdb5           53153       60801    61438976    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x57e9587f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9562    76800000    7  HPFS/NTFS
/dev/sdc2            9562       22616   104857600    7  HPFS/NTFS
/dev/sdc3           22616       30402    62538752    7  HPFS/NTFS

```

Tons of partitions huh? don't worry, most of them are like songs, movies, etc. sda1 is where the mbr. sda5 is my vista partition and obviously sda4 is my linux partition. Oh yeah I have an XP partition on sda6, but I don't think that's relevant in this case, right?

Can anyone help me solve this? I'd greatly appreciate any help

---

### Post by zvacet on 2008-04-19
What is on other two HDD?Do you want to boot them too?Maybe you should read [this.]("http://ubuntuforums.org/showthread.php?t=724817&highlight=boot")

---

### Post by jocko on 2008-04-19
To avoid a kernel update (or anything else that modifies grub) from messing up your menu.lst, find this line:
```
# groot=(hd1,3)
```and change it to:
```
# groot=(hd0,3)
```And then run ```
sudo update-grub
```I'm not absolutely sure about vista, but this section:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
[COLOR=Red]map        (hd0) (hd1)
map        (hd1) (hd0)[/COLOR]
chainloader    +1
```looks like grub tells vista that your hd0 (sda) should be re-mapped to hd1 and the other way around, which makes the vista boot loader think it should find vista on your hdb1?
Try to comment the "map" lines (put a # in front of them) and keep your fingers crossed.

---

### Post by foongkev on 2008-04-19
It contains music, backups, downloads (for torrents), and tons of other files. I like to categorize them as partitions as I have way too many files (doesn't everyone?). No I don't want to boot into them as I put all the non-system/os stuff in there so its easily detachable and I can bring them around without any drama. Thanks zvacet for the helpful link. However I knew 'most' of that stuff already. But I still learnt a few things form the post

> **jocko said:**
> To avoid a kernel update (or anything else that modifies grub) from messing up your menu.lst, find this line:
```
# groot=(hd1,3)
```and change it to:
```
# groot=(hd0,3)
```And then run ```
sudo update-grub
```

I've been doing that as well, but it then screws up the vista boot back to the previous screen I was tlaking about...

> **jocko said:**
> 
I'm not absolutely sure about vista, but this section:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
[COLOR=Red]map        (hd0) (hd1)
map        (hd1) (hd0)[/COLOR]
chainloader    +1
```looks like grub tells vista that your hd0 (sda) should be re-mapped to hd1 and the other way around, which makes the vista boot loader think it should find vista on your hdb1?
Try to comment the "map" lines (put a # in front of them) and keep your fingers crossed.

But this worked perfectly! Thanks so much. I think it was in a way related to my first problem where I had to update grub from hd1 to hd0. I don't know why this happened, but yeah I read other people's menu.lst and they all had that mapping info so I disregarded it as a default coding without analysing it. Don't know why GRUB wants to reverse the drive numbers for loading vista, but commenting them out works perfectly so it isn't reversed! thanks!

---

