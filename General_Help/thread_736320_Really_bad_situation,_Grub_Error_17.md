---
title: "Really bad situation, Grub Error 17"
date: 2008-03-26
forum: General Help
---

### Post by BlackIrish on 2008-03-26
Hi.

First of all I'm really in a panic at the moment. A moment ago I was perfectly running both XP and Ubuntu 7.10, until I needed to create another partition (NTFS).

So I started up PartitionMagic 8, and it needed a reboot so it can create a new 22GB (I think it was 22) partition. So the next thing that happens is my PC is not booting at all, and all I see is Grub Loading Error 17.

Now I've inserted the LiveCD (though this one is from the 64bit ubuntu, while I had the 32bit version installed), and searched through a couple of topics regarding this, but they all were containg some fdisk information and stuff which I don't really know how to use, understand or whether or not they really helped.

I have had years of documents and data on my windows partitions (C and D), and is there any way to get them back? Or is this really serious ???

If it helps, I tried opening the windows partitions in this live cd, and everything seems to be working on them. Also, I had 3 partitions, they were C and D which were NTFS and one which was ext3 and was about 20GB's, and a few minutes ago dunno if it was successful but I tried creating a fourth partition...

Thanks!

P.S. Also here is the fdisk -l info:

> Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x36393638

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       38913   210170362+   f  W95 Ext'd (LBA)
/dev/sda5           12749       35695   184321746    7  HPFS/NTFS
/dev/sda6           35696       38788    24844491   83  Linux
/dev/sda7           38789       38913     1003999+  82  Linux swap / Solaris

---

### Post by danwood76 on 2008-03-26
> 17 : "Invalid device requested"

This error is returned if a device string is recognizable but does not fall under the other device errors.


could you post your menu.lst aswell please?

in the live CD do:
```

cat /boot/grub/menu.lst

```
it looks like your partition table is still there, maybe partition magic broke something.
I tend to steer clear of that software as there are much better tools for partitioning than that load of crap.

---

### Post by BlackIrish on 2008-03-26
Damn, maybe this is even worse? I typed cat /boot/grub/menu.lst in the terminal and this is what I got:

> ubuntu@ubuntu:~$ /boot/grub/menu.lst: No such file or directory
bash: /boot/grub/menu.lst:: No such file or directory
ubuntu@ubuntu:~$ 

Or this way (I guess I made a typo in the first one):

> 
ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory


Maybe the files doesn't exist because I'm on a livecd?

Btw, when we fix this, any recommendation besides Partitionmagic would be great :p

---

### Post by danwood76 on 2008-03-26
oh yeah sorry you need to mount your ext3 partitioon.
do this:
```

sudo mkdir /mnt/temp
sudo umount /dev/sda6
sudo mount -t ext3 /dev/sda6 /mnt/temp

```
you may get an error with the second command as the ext3 partition may not be mounted already, just ignore it.

then this should dump your menu.lst:
```

cat /mnt/temp/boot/grub/menu.lst

```

---

### Post by BlackIrish on 2008-03-26
Yup, this time it worked. Here it is:

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
default         4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# kopt=root=UUID=17b92fcc-a149-445c-824d-b0b0212c3d4e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=17b92fcc-a149-445c-824d-b0b0212c3d4e ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=17b92fcc-a149-445c-824d-b0b0212c3d4e ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,6)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1


---

### Post by sancho panza on 2008-03-26
Try [Super Grub Disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html"). It's a tool for fixing most boot-up issues involving grub, lilo, windows mbr, etc.

---

### Post by danwood76 on 2008-03-26
That looks fine.

I would try to re install grub, this guide is quite good:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Not sure if you would need the 32 bit live CD (not sure if there is 64 bit grub?), if you have the 32 bit live CD it would probably be safer.

About partition magic, I tend to use command line tools to resize partitions as there is more control over what you do. but a lot of people swear by Parted (Gparted is the GUI version) which is available on the ubuntu live CD.
I would also always resize partitions from a live CD as this means no partitions will be mounted when you do the resizing.

---

### Post by BlackIrish on 2008-03-26
danwood76, it worked great! Thanks man!

Although the first time grub didn't want to reinstall, I found some few tweaks and it reinstalled, and now I'm writing this from XP :D

Anyway, everything is working good, now I only have one thing to figure out:

- PartitionMagic did create some kind of partition, because 22GB are missing from my second partition, and it doesn't display in my computer.

Now, I found the partition as some kind of unformatted space, so you say I should try using Parted to get D and the unallocated space together? I'm afraid of using partition magic to merge them, because it can damage grub again...

---

### Post by BlackIrish on 2008-03-26
On second though, I did try using partition magic again (had to :/), because for merging it doesn't require any kind of reboot, and it worked!

All partitions are in place, and everything is working good.

Thanks!

---

### Post by forrestcupp on 2008-03-26
Your problem was that when you added a partition, it changed the reference of where your linux partition is.  So GRUB in your MBR was trying to access its settings off of your old Linux partition's location and it didn't know that you changed it by adding another NTFS partition.  According to your menu.lst, your old partition was (hd0,6).  It looks like it may now be (hd0,5).  You could have changed those entries and it would have worked.

So, this would happen no matter which partitioner you use.  I personally like [GParted LiveCD](http://gparted-livecd.tuxfamily.org/), though.

---

### Post by starcannon on 2008-03-26
Good to hear you got back up and running.
Perhaps a better utility in the future would be gparted, you can install it in ubuntu and then find it in System-->Administration.
There are also liveCD and liveUSB versions available at [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
I like it much better than Partition Magic, and it could even recover your missing 22GB as well as format them to any FS you like.

GL and happy to hear you got your puter back up, I've had the 17 error before myself, I keep /home on its own partition, so I just reinstalled Ubuntu with no important data loss.

---

### Post by Jerry N on 2008-03-26
Congratulations on fixing your problem.  You can get to all your important files and data.  What should you do next? **[SIZE="1"] Backups![/SIZE]  [SIZE="2"]Backups![/SIZE] [SIZE="3"]Backups![/SIZE] [SIZE="4"]Backups![/SIZE] [SIZE="5"]Backups![/SIZE]**  [COLOR="Red"]Remember what Murphy had to say about that situation.[/COLOR]

Jerry

---

