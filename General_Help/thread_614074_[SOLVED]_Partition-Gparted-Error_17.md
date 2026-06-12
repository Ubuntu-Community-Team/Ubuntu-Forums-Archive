---
title: "[SOLVED] Partition-Gparted-Error 17?"
date: 2007-11-15
forum: General Help
---

### Post by squirage on 2007-11-15
Hi All,

  I just need a little hand holding here. I successfully recovered an unknown partition only to bump the linux-swap into /dev/sdb2 and my ext3 partition into /dev/sdb3.

Previously the bad partition, /dev/sdb5, had been inside the extended partition (/dev/sdb1) with the swap as /dev/sdb6. My ext3 partition was /dev/sdb2 and flagged as boot.

Running the LiveCD I can see all partitions and read their contents (yeah!), but as you may have guessed /dev/sdb2 is flagged as boot and I assume that is why I can't load grub because it is trying to boot from the swap.

Question 1: Could I just use Gparted to either move, rename or reflag the partitions and which is the best way?

Question 2: /dev/sdb5 is now surrounded by two small unallocated spaces, one before /dev/sbd1 and one after /sdb5 but still in the extended partition. What is the best way to handle that? (The total unallocated space is only about 6MB.)

Question 3: Does the linux-swap portion need to be encapsulated in the extended portion? Or more directly, where should it reside? I thought I saw some one recommend having the swap be all the way to the right (last) in the list.

Thanks for any thoughts.

---

### Post by meierfra on 2007-11-15
I don't think you need to do any repartitioning. Also grub  does not use the boot flags. So you can leave it at the extended partition. I wouldn't worry about the 6MB unallocated space. Just leave it as it is.

The reason you can't boot is probably that the names of the partitions have changed and the boot loader (grub)  cannot find the ubuntu partition.

To fix this you will have to reinstall grub and edit one or two files.   To tell you exactly what to do, I need some information:

Boot from the live CD and open a terminal (Applications->Accessories->Terminal)
Post the output of the following commands:

```

sudo fdisk -l  

sudo blkid     

cat /boot/grub/menu.lst 

cat /etc/fstab

``` 
(All the l are lower case L, not ones)

---

### Post by meierfra on 2007-11-15
Correction. For the last two commands  you need to mount your ubuntu partitions, say to the folder ubuntu. Then use 

cat  ubuntu/boot/grub/menu.lst 

cat ubuntu/etc/fstab

(I would give you detailed instructions for the mounting, but I need to see  the output of "sudo fdisk -l" first.)

---

### Post by squirage on 2007-11-16
Hi meierfra,

  Thanks for your response. Sorry to take so long getting back to you, I work in the evenings and am going out of town this weekend and will be away from this computer. So if I don't give you an answer right away it is because I can't.

On to the output.

sudo fdisk -l gives:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6bba44a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        9730    76613632    7  HPFS/NTFS

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5d379805

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        5225    41967765    f  W95 Ext'd (LBA)
/dev/sdb2   *        5226        5510     2289220   82  Linux swap / Solaris
/dev/sdb3            5511       12161    53424156   83  Linux
/dev/sdb5               1        5225    41962884+   7  HPFS/NTFS
```

sudo blkid gives:

```
/dev/sda1: UUID="84A4EC25A4EC1C04" LABEL="TOSHIBA SYSTEM VOLUME" TYPE="ntfs" 
/dev/sda2: UUID="F4D6F105D6F0C93E" LABEL="SQ004242V05" TYPE="ntfs" 
/dev/sdb2: UUID="89192e27-9640-4367-b083-c2115ed5ac4d" TYPE="swap" 
/dev/sdb3: UUID="91c2e4ef-d905-4be7-938c-fcbcb4b7669f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="7C7656F77656B19E" TYPE="ntfs" 
```

cat /media/disk/boot/grub/menu.lst gives:

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
default         0

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
# kopt=root=UUID=91c2e4ef-d905-4be7-938c-fcbcb4b7669f ro

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=91c2e4ef-d905-4be7-938c-fcbcb4b7669f ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=91c2e4ef-d905-4be7-938c-fcbcb4b7669f ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, kernel 2.6.20-16-generic
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=91c2e4ef-d905-4be7-938c-fcbcb4b7669f ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet

title           Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=91c2e4ef-d905-4be7-938c-fcbcb4b7669f ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu 7.10, kernel 2.6.17-12-generic
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.17-12-generic root=UUID=91c2e4ef-d905-4be7-938c-fcbcb4b7669f ro quiet splash
initrd          /boot/initrd.img-2.6.17-12-generic
quiet

title           Ubuntu 7.10, kernel 2.6.17-12-generic (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.17-12-generic root=UUID=91c2e4ef-d905-4be7-938c-fcbcb4b7669f ro single
initrd          /boot/initrd.img-2.6.17-12-generic

title           Ubuntu 7.10, kernel 2.6.17-10-generic
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=UUID=91c2e4ef-d905-4be7-938c-fcbcb4b7669f ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet

title           Ubuntu 7.10, kernel 2.6.17-10-generic (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=UUID=91c2e4ef-d905-4be7-938c-fcbcb4b7669f ro single
initrd          /boot/initrd.img-2.6.17-10-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista/Longhorn (loader)
root            (hd0,1)
savedefault
makeactive
chainloader     +1
```

cat /media/disk/etc/fstab gives:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc   proc    defaults        0       0
#Entry for /dev/sdb2 :
UUID=91c2e4ef-d905-4be7-938c-fcbcb4b7669f       /       ext3    defaults,errors=remount-ro      0       1
#Entry for /dev/sda2 :
UUID=F4D6F105D6F0C93E   /media/SQ004242V05      ntfs    defaults,nls=utf8,umask=0222    0       0
#Entry for /dev/sda1 :
UUID=84A4EC25A4EC1C04   /media/TOSHIBA_SYSTEM_VOLUME    ntfs    defaults,nls=utf8,umask=0222    0       0
#Entry for /dev/sdb6 :
UUID=89192e27-9640-4367-b083-c2115ed5ac4d       none    swap    sw      0      0
/dev/cdrom      /media/cdrom0   udf,iso9660     user,noauto     0       0
```

So, if I'm not mistaken, it looks like I need to edit the menu.lst to reflect that sdb3 is now the bootable partition. So change:

```
title           Ubuntu 7.10, kernel 2.6.20-16-generic
root            [COLOR="Red"](hd1,1)[/COLOR]
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=91c2e4ef-d905-4be7-938c-fcbcb4b7669f ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
```

to 

```
title           Ubuntu 7.10, kernel 2.6.20-16-generic
root           [COLOR="Red"] (hd1,2)[/COLOR]
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=91c2e4ef-d905-4be7-938c-fcbcb4b7669f ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
```

Additionally, is it worthwhile to comment out old kernels?

Thanks a lot for your help and direction.

EDIT: The kernel should be 2.6.22-14-generic, for some reason I was focusing on the 16. Otherwise I think I'm right.

---

### Post by meierfra on 2007-11-16
Yes, change all the (hd1,1) to (hd1,2).  Don't forget to change "#groot (hd1,1)# to "#groot (hd1,2)" otherwise you will have problems after the next kernel upgrade.

>  
Additionally, is it worthwhile to comment out old kernels?

Yes. (I would even remove all but the first two  kernels.) And change

# howmany=all

to 

# howmany=2

(howmany=2 says that you want 2 kernels listed in menu.lst. If you leave it at "all", all whose kernels you deleted will reappear after the next kernel upgrade)

You also need to reinstall grub:


```
sudo grub
```

This will give you a "grub>" prompt. Type

```

root (hd1,2)

setup (hd0)

quit
```

That's it. Everything should be back to normal after reboot.

---

### Post by meierfra on 2007-11-16
Just hang on for a second. Edit: I thought I had simpler solutions. But it won't work. So just follow my previous post.

---

### Post by squirage on 2007-11-16
Hi meierfra,

  I used nano to edit menu.lst and was worried that the permissions would get in the way. I realize now that sudo took care of that. I've gotten used to typing sudo for just about every command because I'm still not comfortable with the chmod codes.

  I did what you said, I'm not sure about the setup (hd0) command but it returned something that looked like success.

  I'll cross my fingers and reboot.[-o<

Thanks

---

### Post by squirage on 2007-11-16
Oops,

  I had to deal with my children for a minute while I was trying to restart the system. It ejected the liveCD but the screen is black and the keyboard is unresponsive.:(

  Any thoughts?

---

### Post by squirage on 2007-11-16
Hi meierfra,

  Panic resolved. I don't know why, but the system hung in shutdown. I just held the power button down until it shut off and then restarted.

  System seemed a little slow to boot but it all worked. Now I have my lost partition back and mounted and everything is still there.=D>

  Now back to deciding how best to fix sound, bios bug #81[49435000] and all the video problems I was having.

Thanks again for all your help, the community rules.

---

### Post by meierfra on 2007-11-16
> I used nano to edit menu.lst and was worried that the permissions would get in the way. I realize now that sudo took care of that. I've gotten used to typing sudo for just about every command because I'm still not comfortable with the chmod codes.


Sudo is the correct way to do it. chmod won't help. Instead of "sudo nano" you could have used "gksudo gedit". That opens a new windows and gives you a nicer editor.

> I had to deal with my children for a minute while I was trying to restart the system. It ejected the liveCD but the screen is black and the keyboard is unresponsive

No idea. Must be the kids' fault :). If it happens again, you might want to start a new thread on that.

---

