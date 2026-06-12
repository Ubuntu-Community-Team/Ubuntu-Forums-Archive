---
title: "Log is being saved in /var/log/fsck/checkfs"
date: 2007-12-29
forum: General Help
---

### Post by Skarjoko on 2007-12-29
After reinstalling Arch Linux on my second partition, I keep getting this message when I try to boot up Ubuntu:

failed( code 8 )
A log is being saved in /var/log/fsck/checkfs, please try to fix this problem manually (or something similar).

And it drops me into a command prompt. I can exit it and resume the boot with Ctrl+d, but it's getting pretty annoying now, and I'd like to know how I can resolve this problem. I didn't install grub when I installed Arch, I just added an entry for it in grub. 

Thanks.

EDIT: Before the failed( code 8 ), it says something about not being able to load the UUID.

---

### Post by plucky on 2007-12-30
Skarjoko

This problem happens when the **UUID** in **/etc/fstab** does not match the new uuid created when you install ARCH.

To fix open a terminal and type ```
blkid
```. This will display the **UUID** for all your partitions. Then ```
gksudo gedit /etc/fstab
``` and copy and paste the correct UUID for the partition that fails.

Hope this helps

---

### Post by Skarjoko on 2007-12-31
The UUID from blkid gives the same UUID in my /etc/fstab, for the partition that fails.

Also, I actually made a mistake in my first post. It says it could not resolve the UUID, not load the UUID. And I also have 2 other partitions in my fstab that say: /dev/ !! UNKOW DEVICE !!, instead of /dev/sda5 and /dev/sda7. Is uh, that normal?

---

### Post by plucky on 2007-12-31
Ok, perhaps it is failing the file system check on boot.

Open the log file and post results,maybe you need to run **fsck** on the failing partition

```
gedit /var/log/fsck/checkfs
``` copy and post

Good luck

---

### Post by Skarjoko on 2008-01-01
I ran fsck a while ago, although I don't exactly remember what it did. It certainly didn't solve the problem though...

Here is my current log:

> fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Unable to resolve 'UUID=c339e8fc-78d8-4bd7-88f7-30c683cd3efb'

fsck died with exit status 8

I'll edit this post with the log after I run fsck.

---

### Post by Skarjoko on 2008-01-03
So I run fsck when the command prompt comes up, and I say yes to 'it may mess up your system', and it fails with some sort of error which I didn't quite catch. After I ran it, I type in 'reboot' and it just continues the boot-up, which leads to X not starting (gives me a blue screen telling me X will not start). I reboot, and it automatically runs a check on my filesystem, fixing an inode that had a zero dtime. It tells me to run fsck manually after failing at a ( code 4 ) and reboot. I run fsck, but again, when I try to reboot it just continues the startup. X won't start, and I reboot my system. This time the automatic fsck didn't find anything, and I came back to the failed( code 8 ) error and command prompt.

So I'm back to where I was. Isn't there any way to NOT use UUID, and just the regular root=/dev/sda6? Or is there a way I can fix this?

---

### Post by plucky on 2008-01-03
> Isn't there any way to NOT use UUID, and just the regular root=/dev/sda6?

You can replace the UUID for each partition by the device name
```
gksudo gedit /etc/fstab
```

Replace **UUID=c339e8fc-78d8-4bd7-88f7-30c683cd3efb** by its device name obtained using **blkid** e.g **/dev/hda6** or whatever

Can you copy and paste these commands to this thread
```
sudo fdisk -l
``` that is lower case L not 1
```
cat /etc/fstab
```
```
cat /boot/grub/menu.lst
```
```
ls -l /dev/disk/by-uuid
```
> And I also have 2 other partitions in my fstab that say: /dev/ !! UNKOW DEVICE !!, instead of /dev/sda5 and /dev/sda7. Is uh, that normal?

No that is not normal. Could be your problem

Cheers

---

### Post by Foxman2k on 2008-01-03
For what it's worth,  I am having the exact same problem after install Linux Mint on a seperate drive....

My problem is on /dev/sdb3 - My home partition.  fsck fails during boot,  dropping me to a maintenance shell.

```

slincoln@slincoln-desktop:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa43c228e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1218     9783553+  83  Linux
/dev/sda2            1219        7297    48829567+  83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x86af86af

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2550    20482843+  83  Linux
/dev/sdb2            2551        2703     1228972+  82  Linux swap / Solaris
/dev/sdb3            2704       30401   222484185   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux
slincoln@slincoln-desktop:~$ 

```

```

slincoln@slincoln-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=3d734ac1-7e47-4b7f-8e8b-a75e38447ed6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb3
UUID=6d1f3d59-7d46-4136-9891-8fbe3d0295b8 /home           ext3    defaults        0       2
# /dev/sda1
UUID=ded48375-0285-44d0-98f2-e1448e5017da /media/linux    ext3    defaults        0       2
# /dev/sdb2
UUID=993821f2-cdb0-43ac-86df-5c675b9d2548 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
slincoln@slincoln-desktop:~$ 

```

```

slincoln@slincoln-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=3d734ac1-7e47-4b7f-8e8b-a75e38447ed6 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3d734ac1-7e47-4b7f-8e8b-a75e38447ed6 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3d734ac1-7e47-4b7f-8e8b-a75e38447ed6 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=ded48375-0285-44d0-98f2-e1448e5017da ro quiet splash 
initrd          /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=ded48375-0285-44d0-98f2-e1448e5017da ro single 
initrd          /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu 7.10, memtest86+ (on /dev/sda1)
root            (hd0,0)
kernel          /boot/memtest86+.bin  
savedefault
boot

slincoln@slincoln-desktop:~$ 

```

```

slincoln@slincoln-desktop:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2008-01-03 09:25 1cc42cce-d02f-4dce-a907-0666ad009ac2 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-01-03 09:25 3d734ac1-7e47-4b7f-8e8b-a75e38447ed6 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-01-03 09:25 5e5724f3-2e00-4b8a-abbe-f39ce987b0cf -> ../../sdc1
lrwxrwxrwx 1 root root 10 2008-01-03 09:25 6d1f3d59-7d46-4136-9891-8fbe3d0295b8 -> ../../sdb3
lrwxrwxrwx 1 root root 10 2008-01-03 09:25 993821f2-cdb0-43ac-86df-5c675b9d2548 -> ../../sdb2
lrwxrwxrwx 1 root root 10 2008-01-03 09:25 f09542fe-1fbd-4888-af83-478bee385292 -> ../../sda2
slincoln@slincoln-desktop:~$ 

```

---

### Post by plucky on 2008-01-03
Foxman2,

Which distro did you boot into to get this data?
and
Which distro boot causes the failure?

I assume Ubuntu boots from **sda1** and linux mint boots from **sdb1**

This is the only problem that I see

```
# /dev/sda1
UUID=[color=red]ded48375-0285-44d0-98f2-e1448e5017da[/color] /media/linux    ext3    defaults        0       2
lrwxrwxrwx 1 root root 10 2008-01-03 09:25 **1cc42cce-d02f-4dce-a907-0666ad009ac2** -> ../../sda1
```

---

### Post by Foxman2k on 2008-01-03
> **plucky said:**
> Foxman2,

Which distro did you boot into to get this data?
and
Which distro boot causes the failure?

I assume Ubuntu boots from **sda1** and linux mint boots from **sdb1**

This is the only problem that I see

```
# /dev/sda1
UUID=[color=red]ded48375-0285-44d0-98f2-e1448e5017da[/color] /media/linux    ext3    defaults        0       2
lrwxrwxrwx 1 root root 10 2008-01-03 09:25 **1cc42cce-d02f-4dce-a907-0666ad009ac2** -> ../../sda1
```

sda1 -> Linux Mint ( I just happen to have Mint on it,  I use this partition to try out stuff)
sda2 -> Data Partition

sdb1 -> Ubuntu root partition
sdb3 -> Home Partition

sbc -> Removable USB drive

The error pops up when booting into Ubuntu.

---

### Post by Foxman2k on 2008-01-03
Here is the grub menu.lst on the Linux Mint partition....

```

slincoln@slincoln-desktop:/media/tmp/boot/grub$ cat menu.lst 
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
default         0

gfxmenu=/etc/grub/message.mint

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# kopt=root=/dev/sda1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title           Linux Mint, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
boot

title           Linux Mint, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.22-14-generic
boot

title           Linux Mint, kernel memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title           Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sdb1)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3d734ac1-7e47-4b7f-8e8b-a75e38447ed6 ro quiet splash 
initrd          /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sdb1)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3d734ac1-7e47-4b7f-8e8b-a75e38447ed6 ro single 
initrd          /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title           Ubuntu 7.10, memtest86+ (on /dev/sdb1)
root            (hd1,0)
kernel          /boot/memtest86+.bin  
savedefault
boot

```

---

### Post by plucky on 2008-01-04
Foxman2k

You need to boot into Ubuntu and compare the **ls -l /dev/disk/by-uuid** output to what is in the **cat /etc/fstab** file in Ubuntu.The problem is that the UUID has changed when you installed linux mint and the **fstab** file hasn't been updated.

You should be able to get past the dropping into maintenance shell by a Ctrl D and enter and it should continue to boot. If it doesn't you should be able to access that file from linux mint.

Hope this makes sense

---

### Post by Foxman2k on 2008-01-04
Running Ubunut now...

```

slincoln@slincoln-desktop:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2008-01-03 09:25 1cc42cce-d02f-4dce-a907-0666ad009ac2 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-01-03 09:25 3d734ac1-7e47-4b7f-8e8b-a75e38447ed6 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-01-03 09:25 5e5724f3-2e00-4b8a-abbe-f39ce987b0cf -> ../../sdc1
lrwxrwxrwx 1 root root 10 2008-01-03 09:25 6d1f3d59-7d46-4136-9891-8fbe3d0295b8 -> ../../sdb3
lrwxrwxrwx 1 root root 10 2008-01-03 09:25 993821f2-cdb0-43ac-86df-5c675b9d2548 -> ../../sdb2
lrwxrwxrwx 1 root root 10 2008-01-03 09:25 f09542fe-1fbd-4888-af83-478bee385292 -> ../../sda2
slincoln@slincoln-desktop:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=3d734ac1-7e47-4b7f-8e8b-a75e38447ed6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb3
UUID=6d1f3d59-7d46-4136-9891-8fbe3d0295b8 /home           ext3    defaults        0       2
# /dev/sda1
UUID=ded48375-0285-44d0-98f2-e1448e5017da /media/linux    ext3    defaults        0       2
# /dev/sdb2
UUID=993821f2-cdb0-43ac-86df-5c675b9d2548 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
slincoln@slincoln-desktop:~$ 

```

Am I blind,  or are they they not the same?

---

### Post by Foxman2k on 2008-01-04
```

slincoln@slincoln-desktop:~$ cat /var/log/fsck/checkfs 
Log of fsck -C -R -A -a 
Thu Jan  3 09:25:27 2008

fsck 1.40.2 (12-Jul-2007)
/dev/sdb3: clean, 92733/27820032 files, 40307162/55621046 blocks
fsck.ext3: Unable to resolve 'UUID=ded48375-0285-44d0-98f2-e1448e5017da'
fsck died with exit status 8

Thu Jan  3 09:25:27 2008
----------------
slincoln@slincoln-desktop:~$ 

```

---

### Post by plucky on 2008-01-04
Foxman2k,

Checkout the UUID's for sda1,they are different,

```
lrwxrwxrwx 1 root root 10 2008-01-03 09:25 1cc42cce-d02f-4dce-a907-0666ad009ac2 -> ../../sda1

# /dev/sda1
UUID=ded48375-0285-44d0-98f2-e1448e5017da /media/linux    ext3    defaults        0       2
```

You need to edit /etc/fstab and replace **ded48375-0285-44d0-98f2-e1448e5017da** with **1cc42cce-d02f-4dce-a907-0666ad009ac2**

Good luck

---

### Post by Skarjoko on 2008-01-08
Well after changing the UUID's around a bit, I finally got it to work. I'm not sure exactly what was wrong, but I'm guessing the settings for /dev/sda7 and /dev/sda8 were switched around or something. 

Thanks for all the help.

---

