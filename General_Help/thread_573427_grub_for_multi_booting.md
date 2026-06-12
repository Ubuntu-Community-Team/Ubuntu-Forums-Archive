---
title: "grub for multi booting"
date: 2007-10-11
forum: General Help
---

### Post by clinto on 2007-10-11
Well, I posted this in an old thread and it wasn't getting any attention, so...
-------------------

Well, I have a new problem now. :D

I had Ubuntu installed on one partition and decided to set up openSUSE 10.2 on another one. I let it create it's own Grub and figured I could just edit Ubuntu in later.

Apparently, openSUSE installs Grub a little differently than Ubuntu does. For example, I'll put both menu.lst files up. First the one from Ubuntu:

```

abnerdoon@koenigdesk:/boot/grub$ cat menu.lst

default         0
color cyan/blue blink-white/blue



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
# kopt=root=/dev/hdb6 ro

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
# defoptions=

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

#title          Debian GNU/Linux, kernel 2.6.20-16-generic
#root           (hd1,0)
#kernel         /vmlinuz-2.6.20-16-generic root=/dev/hdb6 ro 
#initrd         /initrd.img-2.6.20-16-generic
#boot

#title          Debian GNU/Linux, kernel 2.6.20-16-generic (recovery mode)
#root           (hd1,0)
#kernel         /vmlinuz-2.6.20-16-generic root=/dev/hdb6 ro single
#initrd         /initrd.img-2.6.20-16-generic
#boot

#title          Debian GNU/Linux, kernel 2.6.20-15-generic
#root           (hd1,0)
#kernel         /vmlinuz-2.6.20-15-generic root=/dev/hdb6 ro 
#initrd         /initrd.img-2.6.20-15-generic
#boot

#title          Debian GNU/Linux, kernel 2.6.20-15-generic (recovery mode)
#root           (hd1,0)
#kernel         /vmlinuz-2.6.20-15-generic root=/dev/hdb6 ro single
#initrd         /initrd.img-2.6.20-15-generic
#boot

#title          Debian GNU/Linux, kernel memtest86+
#root           (hd1,0)
#kernel         /memtest86+.bin 
#boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title           Microsoft Windows XP Home Edition on hda1
root            (hd0,0)
savedefault
makeactive
chainloader     +1

title           Ubuntu Feisty(kernel 2.6.20-16-generic) on hdb6
root            (hd1,0)
kernel          /vmlinuz-2.6.20-16-generic root=/dev/hdb6 ro 
initrd          /initrd.img-2.6.20-16-generic
boot

title           Ubuntu Feisty(recovery mode)
root            (hd1,0)
kernel          /vmlinuz-2.6.20-16-generic root=/dev/hdb6 ro single
initrd          /initrd.img-2.6.20-16-generic
boot

title           memtest86+
root            (hd1,0)
kernel          /memtest86+.bin 
boot

```

Now the one from openSUSE:

```

abnerdoon@koenigdesk:/home/hdb7/boot/grub$ sudo cat menu.lst
# Modified by YaST2. Last modification on Tue Oct  9 18:50:58 EDT 2007
default 0
timeout 8
gfxmenu (hd1,6)/boot/message

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 10.2
    root (hd1,6)
    kernel /boot/vmlinuz-2.6.18.2-34-default root=/dev/hdb7 vga=0x31a resume=/dev/hdb2 splash=silent showopts
    initrd /boot/initrd-2.6.18.2-34-default

title Ubuntu 7.04
    kernel (hd1,0)/vmlinuz-2.6.20-16-generic root=/dev/hdb6 vga=0x31a resume=/dev/hdb2
    initrd (hd1,0)/initrd.img-2.6.20-16-generic

###Don't change this comment - YaST2 identifier: Original name: windows###
title Windows
    rootnoverify (hd0,0)
    chainloader (hd0,0)+1

###Don't change this comment - YaST2 identifier: Original name: floppy###
title Floppy
    rootnoverify (hd0,0)
    chainloader (fd0)+1

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 10.2
    root (hd1,6)
    kernel /boot/vmlinuz-2.6.18.2-34-default root=/dev/hdb7 vga=normal showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off 3
    initrd /boot/initrd-2.6.18.2-34-default


```

NOTICE! I have the /boot for Ubuntu on the first partition of the second hard drive. Yeah, my crap is a mess and I should probably just start all over again. :/

The Ubuntu 7.04 section is what I added. With this, I was able to boot into Ubuntu from the boot loader. However, I get a filesystem error while it tries to boot into it's partition. Does anyone know why this might be? I'm sure it has something to do with the way grub is set up differently. I'm just not sure what exactly the problem is. Thanks.

---

### Post by dcstar on 2007-10-11
> **clinto said:**
> 
...........
The Ubuntu 7.04 section is what I added. With this, I was able to boot into Ubuntu from the boot loader. However, I get a filesystem error while it tries to boot into it's partition. Does anyone know why this might be? I'm sure it has something to do with the way grub is set up differently. I'm just not sure what exactly the problem is. Thanks.

Try getting rid of the "resume" stuff in the Ubuntu entry - it is not there in the original stuff.

---

### Post by rsambuca on 2007-10-11
and you should have a line defining 'root'

---

### Post by clinto on 2007-10-12
> **rsambuca said:**
> and you should have a line defining 'root'
Oh snap! wtf. I had it in there before... I don't know what happened with that. Hmm. See, I changed it using the gui tool in Suse. I wonder if it didn't alter it after I got done with it.

And thanks dcstar. I'll try it. I'm not sure why that is there. hdb2 is my swap partition.

---

### Post by clinto on 2007-10-14
Okay, first off, every time I run openSUSE, it rewrites grub and takes away the root(x,x) under ubuntu. Either way, Ubuntu boots the same.

I'm pretty sure it's a UUID conflict. This is the output sent to /var/log/fsck/checkfs:
```

Log of fsck -C -R -A -a 
Sun Oct 14 01:18:53 2007

fsck 1.40-WIP (14-Nov-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hda5: 91 files, 309831/1341115 clusters
/dev/hdb1: clean, 46/26208 files, 42862/104420 blocks
/dev/hdb4: clean, 247/18464768 files, 5612503/36901297 blocks
/dev/hdb5: clean, 5909/12812288 files, 13294582/25599569 blocks (check in 5 mounts)
fsck.ext3: Unable to resolve 'UUID=6e98ae6f-9595-450f-af19-9f20c75c5df8'

/dev/hdb8: clean, 11/2562240 files, 124489/5118702 blocks
fsck died with exit status 8

Sun Oct 14 01:18:55 2007
----------------

```

I don't get what it's telling me it was unable to resolve. I'm assuming it is hdb6, which is where Ubuntu is, but it doesn't say that. And hdb7, where openSUSE is located, isn't in that check.

openSUSE's grub setup doesn't use UUIDs as you can see from my previous post. What am I supposed to do? I'm not looking for a quick fix, I really want to learn this stuff.

---

### Post by meierfra on 2007-10-14
Could you post the output 

```
cat /etc/fstab
```
and 

```
sudo blkid
```
 from an Ubuntu terminal. (I 'm assuming the error occurs while booting into Ubuntu, if not use a Suse terminal)

---

### Post by clinto on 2007-10-15
I can get into ubuntu by pressing ctrl+D when it prompts me to repair the filesystem. Here's my fstab:

```

abnerdoon@koenigdesk:/var/log/fsck$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb6
UUID=097f966e-f64a-447e-bb49-da7d0124a02b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb1
UUID=40bf9948-b1d9-4d63-9ad8-fc9b394793e1 /boot           ext3    defaults        0       2
# /dev/hda1
UUID=0000000083FC3F26 /home/WindowsXP     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=C5FA-6099  /home/WindowsVFAT     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb4
UUID=8f044c31-519d-47de-a93d-d139110bbc53 /home/hdb4     ext3    defaults        0       2
# /dev/hdb5
UUID=f8a16bff-bd1e-45b7-81bf-68709c4ba0a8 /home/USV     ext3    auto,rw,user,sync        0       2
# /dev/hdb7
UUID=6e98ae6f-9595-450f-af19-9f20c75c5df8 /home/openSUSE     ext3    defaults        0       2
# /dev/hdb8
UUID=f47c2228-4d9b-4218-b041-445302d91d56 /home/hdb8     ext3    defaults        0       2
# /dev/hdb2
UUID=98889f1c-9628-4ac4-a9af-7625d98cf298 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

```

abnerdoon@koenigdesk:/var/log/fsck$ sudo blkid
Password:
/dev/hda1: TYPE="ntfs" 
/dev/hda5: LABEL="DISE_BACKUP" UUID="C5FA-6099" TYPE="vfat" 
/dev/hdb1: UUID="40bf9948-b1d9-4d63-9ad8-fc9b394793e1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdb2: UUID="98889f1c-9628-4ac4-a9af-7625d98cf298" TYPE="swap" 
/dev/hdb4: UUID="8f044c31-519d-47de-a93d-d139110bbc53" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdb5: UUID="f8a16bff-bd1e-45b7-81bf-68709c4ba0a8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdb6: UUID="097f966e-f64a-447e-bb49-da7d0124a02b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdb7: UUID="36a61694-164f-4200-809d-9783d272bcc1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdb8: UUID="f47c2228-4d9b-4218-b041-445302d91d56" SEC_TYPE="ext2" TYPE="ext3" 

```

OMG YOU DON'T KNOW HOW LONG I'VE BEEN SEARCHING FOR THAT COMMAND! Thank you so much. I went everywhere trying to find that command. I went on the IRC channel even, and no one could help me.

So I'm guessing my problem isn't with grub, but with my fstab file, correct?

---

### Post by rsambuca on 2007-10-15
Your hdb7 has an incorrect UUID in the fstab.  You can correct it, or you can just remove it and use the /dev/hdb7 convention instead.  Both will work.

Also, another means of getting UUID's is

ls /dev/disk/by-uuid/ -alh

---

### Post by clinto on 2007-10-15
thanks everyone, that's what the problem was.

I really appreciate it. I've learned a few things that I can share.

---

