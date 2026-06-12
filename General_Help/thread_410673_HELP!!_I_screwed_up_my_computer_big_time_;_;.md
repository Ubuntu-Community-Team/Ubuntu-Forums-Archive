---
title: "HELP!! I screwed up my computer big time ;_;"
date: 2007-04-16
forum: General Help
---

### Post by pingpongboss on 2007-04-16
I was trying to install grub-gfxboot under feisty, trying to get a cooler looking grub menu, but I managed to screw up my entire computer, including the windows partition.

First, I think i entered the wrong thing for the (hdax,y) for "install-grub", but the gfxboot worked. I had the nice looking boot menu. But the problem was that I couldn't boot into my windows partition even though the ubuntu partition worked. I tried my best to look through the 30+ pages of that thread and a couple of posts suggested that use the Windows Rescue Console thing and run fixboot and fixmbr (since i thought maybe I overwrote the windows MBR while trying to install the new grub).

Well, I did that, but now when I reboot I can neither boot into ubuntu nor windows >_<. Grub doesnt show up anymore (like i expected) but Windows doesnt work either. It gives me a NTLDR is missing error and I have to restart. I tried to fix the NTLDR issue but it looks like that won't work because something made my windows partition retarded.

I booted using a Feisty livecd to see if i can recover some files on the windows partition. Check this mess out:

[[IMG]http://img352.imageshack.us/img352/3997/screenshotvy4.th.png[/IMG]](http://img352.imageshack.us/my.php?image=screenshotvy4.png)

Hooly crud. I'm looking into re-enabling grub as the bootloader, but I don't have much hope for recovering my windows partition. Is there a way to give me access to the partition again, or even let me save some files from it? I really have no clue what to do next.

---

### Post by dfreer on 2007-04-16
wow that screenshot is,,, interesting, I have no idea what would cause that... was this a NTFS partition? if so, were you using NTFS3G or something similiar?

my guess would be that you installed GRUB to the windows partition, instead of to the MBR or the linux partition. This might explain why windows wouldn't boot but ubuntu would (it would have overwrote the NTLDR and boot sector on the windows partition). It might also explain the gobblegook you see from the linux livecd. You should be able to still use the Ubuntu partition if this is the case (use a livecd to reinstall GRUB to the MBR), but I dunno about windows... *poof*

---

### Post by Famicommie on 2007-04-16
Try reinstalling GRUB and booting into Ubuntu again. Then, mount your Windows partition, and see if you can copy the files you need saved over to your Linux partition.

---

### Post by pingpongboss on 2007-04-16
thank you very much for the quick replies. Yes, my windows partition was ntfs and what you (dfreer) described is pretty much what happened as far as I know. 

I googled for how to reinstall grub as you two suggested but haven't found one that worked with what I had (some tell me to boot into text-only mode, but i cant boot into ANYTHING). Anyone know a good grub-reinstall howto off the top of their head? thx alot

---

### Post by louistan3 on 2007-04-16
uhmmm.. if u are able to mount it...

then i thnk u could copy your files using the CLI.. 

if it says permission denied or smthn.. u might need to enable root.. 

i thnk to enable it type 

```
sudo passwd root
```

then it asks you to enter a new passwd for root..

after that

```
su
```

enter your password and ur root..

anyway.. im not sure.. but its the only way i could thnk of right now.. 
il try to find another way..

---

### Post by dfreer on 2007-04-16
hmmm you'll need to use a livecd of some sort, access the terminal:

this should help:
[http://ubuntuforums.org/showpost.php?p=117829&postcount=2](http://ubuntuforums.org/showpost.php?p=117829&postcount=2)

---

### Post by dfreer on 2007-04-16
> **louistan3 said:**
> uhmmm.. if u are able to mount it...

then i thnk u could copy your files using the CLI.. 

if it says permission denied or smthn.. u might need to enable root.. 

i thnk to enable it type 

```
sudo passwd root
```

then it asks you to enter a new passwd for root..

after that

```
su
```

enter your password and ur root..

anyway.. im not sure.. but its the only way i could thnk of right now.. 
il try to find another way..

not exactly sure of what you are trying to tell him to do here. you definitely wouldn't need to enable the root password, just use sudo <command>. if you want to be root you can do a sudo su and still not need the root password enabled (it's a security risk).

---

### Post by breezyfox on 2007-04-16
[QUOTE=pingpongboss;2460800]I was trying to install grub-gfxboot under feisty, trying to get a cooler looking grub menu, but I managed to screw up my entire computer, including the windows partition.

Hi.
Yes you can recover the installed windows if nothing worse has happened to the windows partition. Your windows will boot.
You need to use super grub disk. just make a floppy and boot it up with suer grub floppy. it will search any installed grub and windows partition. I have tested it , it works.

[http://www.cyberciti.biz/tips/wp-content/uploads/2006/10/super-grub-disk-linux-options.png](http://www.cyberciti.biz/tips/wp-content/uploads/2006/10/super-grub-disk-linux-options.png)

you can find many other links. main link is not working right now. serch super grub.

BZ

---

### Post by pingpongboss on 2007-04-16
thanks guys i'll try that when i get back home. One problem with BreezyFox's method is the my laptop does not have a floppy drive and i doubt i can boot off of a USB floppy adapter thingy if i can find one. Only thing i can boot from is a LiveCD >_<

---

### Post by pingpongboss on 2007-04-16
thx alot dfreer! I restored grub (grub-gfxboot actually) and I can boot fine into ubuntu. Windows is still not working though. If i select it from the grub menu, it gives me the NTLDR is missing error. As I boot up ubuntu, i notice that it says Mounting local partitions (or something like that) ... FAILED. And i verify on my desktop that I can't seem to mount the sda1 partition which is my windows partition. 

Is there a sudo mount command that force-mounts? If i mount regularly, i get this error
```
$ sudo mount /media/sda1
NTFS signature is missing.
Failed to startup volume: Invalid argument
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

For some reason, nothing is recognizing that it's an NTFS partition. WHen i was using the Windows Recovery Console thing, it couldn't detect that I had a windows installation anywhere on my harddrive and when i ran fixboot or fixmbr (one of those) it said that the partition was detected as FAT32. wtf..

Any way i can recover the partition?

---

### Post by breezyfox on 2007-04-16
hi try gpart which is a partition recovery utility built in ubuntu.

try to install from synaptic it is gpart and not gparted. and try to scan the drives.

gpart /dev/hda

or

gpart /dev/sda          what ever the case is.

also use grub commandline.

root terminal > grub > geometry (hd0)

it will give you some better idea.

bz

---

### Post by Bert Mariën on 2007-04-16
If you have a floppy drive AND a DOS boot disk, do this:

1 Boot from the floppy
2 Type
fdisk /mbr
3 reboot

Your windows should be back, but GRUB will have disappeared.
You'll have to reinstall GRUB afterwards.

---

### Post by Bert Mariën on 2007-04-16
If you should not have a boot disk, you'll find some here:

[http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm)

A win98 disk will do just fine.

---

### Post by Bert Mariën on 2007-04-16
You can also find some more specific disks here:

[http://www.cnomy.com/?dn=startdisk.com&pid=1PO106XG2](http://www.cnomy.com/?dn=startdisk.com&pid=1PO106XG2)

---

### Post by pingpongboss on 2007-04-16
hi breezyfox, I ran what you suggested, and my suspicion that it is unrecoverable is now deeper. Here is the output from the gpart and grub commands:

Grub:
```
grub> geometry (hd0)
drive 0x80: C/H/S = 9729/255/63, The number of sectors = 156301488, /dev/sda
  ** Partition num: 0,  Filesystem type unknown, partition type 0x7**
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 5,  Filesystem type unknown, partition type 0x82

grub> 

```

Gpart:
```
$ sudo gpart /dev/sda

Begin scan...
**Possible partition(DOS FAT), size(10mb), offset(0mb)**
Possible partition(Linux ext2), size(19320mb), offset(49999mb)
Possible extended partition at offset(69319mb)
   Possible partition(Linux ext2), size(6487mb), offset(69319mb)
   Possible partition(Linux swap), size(509mb), offset(75806mb)
End scan.

Checking partitions...
**Partition(Primary DOS with 12 bit FAT): primary **
Partition(Linux ext2 filesystem): primary 
   Partition(Linux ext2 filesystem): logical 
   Partition(Linux swap or Solaris/x86): logical 
Ok.

Guessed primary partition table:
[B]Primary partition(1)
   type: 001(0x01)(Primary DOS with 12 bit FAT)
   size: 10mb #s(20739) s(63-20801)
   chs:  (0/1/1)-(1/75/12)d (0/1/1)-(1/75/12)r[/B]

Primary partition(2)
   type: 131(0x83)(Linux ext2 filesystem)
   size: 19320mb #s(39568088) s(102398310-141966397)
   chs:  (1023/254/63)-(1023/254/63)d (6374/0/1)-(8836/254/56)r

Primary partition(3)
   type: 015(0x0F)(Extended DOS, LBA)
   size: 6997mb #s(14329980) s(141966405-156296384)
   chs:  (1023/254/63)-(1023/254/63)d (8837/0/1)-(9728/254/63)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
```

I bolded what I thought should have been my windows partition. It is beign detected as DOS/FAT but I am certain that it is a NTFS partition. I'll include a SS of what the GParted GUI shows for those who want to see how my partitions are laid out.

[[IMG]http://img153.imageshack.us/img153/9669/screenshotdevsdagpartedfk8.th.png[/IMG]](http://img153.imageshack.us/my.php?image=screenshotdevsdagpartedfk8.png)

And Bert Marien, I don't have a floppy drive that I can boot from, but thanks for the help anyways. Thanks again breezyfox. Do you guys think i have a chance at recovering this partition?

---

### Post by dfreer on 2007-04-16
basically, the problem ISN'T that the windows boot loader is missing, it's that the windows partition is either corrupted or incorrectly reported as FAT instead of NTFS.

pingpongboss, I would look for a program that can let you manually edit your partition tables (make SURE you know what you are doing otherwise you will lose more than your windows partition). Try manually changing it to report it as NTFS, or perhaps see if there is a way to force fstab to mount the partition as NTFS regardless of what it says. I'm thinking that without professional help you may never recover that data :( 

These are all troubleshooting ideas though, I've never encountered this problem before so don't take my word as facts, eh?

---

### Post by breezyfox on 2007-04-17
Hi

I somehow agree with dfreer that windows partition may become corrupted or some how reporting wrong.
**A.**
Few solutions comes to my mind at this time:
[COLOR="black"]A.[/COLOR]
If you have windows cd, why not update with that. it will not destroy your "documents and setting folder". your all documents will remain as it is. But you have to install service pack2 again. ( i think so, that should't be a big deal as compared to loss of documents. 
Make sure you do not click on install a fresh copy of windows. I think it a repair option (second one). i can find out later if u want to try that.

**b**
 to see and have a look at your documents in any partition whather it is FAT, fat32, linux or resiesers an deven ntfs.  Use Puppy linux live cd. it is a very small destro. 70-80 mb. download iso and burn it to cd.
Boot from this cd ( you wil love it). it has graphical options to mount any partition and recognises any partition. Now you will be able to see all your files, it that all exists (i hope exists)

YOu can then mount your windows partitition as read and write and copy your stuff where ever you want. this options i think is best at this movements because we not touching the partions and leaving it as such. (repairing by windows it may cause any thing wrong , so we are not considering that option as first one. This will give you can fair idea if you documnts still exists.

 it looks like that your partions is deleted and another fat16 have been created at the same place. ( i wish i am wrong). conversion from ntfs to fat16 or fat32 is destructive but  not the other way around.
try pupy cd and let us know. All the best.

can you post you menu.lst file out put from /boot/grub/menu.lst.  SATA dive have different settings there.

bz

---

### Post by pingpongboss on 2007-04-17
here's the menu.lst file:

```
$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         5

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=10ea4b77-b0e6-4e0b-8427-8abd2a17a2a0 ro

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
# defoptions=rootflags=data=writeback elevator=cfq splash

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
# altoptions=(recovery mode) single rootflags=data=writeback elevator=cfq

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

gfxmenu /boot/grub/message.new

#splashimage=(hd0,1)/boot/grub/splash.xpm.gz

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=10ea4b77-b0e6-4e0b-8427-8abd2a17a2a0 ro rootflags=data=writeback elevator=cfq splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=10ea4b77-b0e6-4e0b-8427-8abd2a17a2a0 ro single rootflags=data=writeback elevator=cfq
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

I will try puppy linux livecd asap, i hope it's not the destructive conversion to FAT16 that you mentioned :x

what is in puppy linux that allows me to attempt to mount and recognize any partition? Is it something i can install in Ubuntu? thanks for your help

---

### Post by Bert Mariën on 2007-04-17
Puppy has a small graphical program to mount disks. I believe there is a short cut on the desktop just called "disks". But I'm not completely sure. There is short cut on the desktop though.

---

### Post by grg3 on 2007-04-17
Before you give up and reinstall Windows, try this from the xprescue console (boot xp cd go to rescue)

I messed up a partition table once and this fixed it. Might help.

FIXMBR C:
FIXBOOT C:
COPY CDDrive:\I386\NTLDR C:\
COPY CDDrive:\I386|NTDETECT.COM C:\
BOOTCFG /rebuild

---

### Post by Sef on 2007-04-17
Check out [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").  It can recover lost partitions.

---

### Post by pingpongboss on 2007-04-17
thank you grg3 and sef, i'll be trying that when I get home

---

