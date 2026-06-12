---
title: "Installing Burg on Ubuntu Live USB"
date: 2013-01-15
forum: General Help
---

### Post by hadora on 2013-01-15
Hello,

I'm Trying to install Burg on Ubuntu live usb but i can't seem to succeed 
i followed several guide but every time there is a different error it starting to drive me crazy :(

My Flash drive is formated in NTFS and i installed Ubuntu 12.10 with YUMI
I followed this guide
[http://ubuntuforums.org/showthread.php?t=1954223](http://ubuntuforums.org/showthread.php?t=1954223)

But when i type chroot /mnt/ /bin/bash i get the error  " no such file or directory "

What i'm doing wrong ?

---

### Post by hadora on 2013-01-15
Just to add some information

The path of the ubuntu live is 
S:\multiboot\ubuntu1210
 on S:\multiboot there is the grub files
chain.c32  grub.exe memdisk syslinux.cfg vesamenu.c32 yumi

On the racine of the Flash disk
there is folders that i created with 
> mount --bind /bin ./bin
mount --bind /cdrom ./cdrom
mount --bind /dev ./dev
mount --bind /dev/pts ./dev/pts
mount --bind /etc ./etc
mount --bind /home ./home
mount --bind /lib ./lib
mount --bind /media ./media
mount --bind /proc ./proc
mount --bind /rofs ./rofs
mount --bind /sbin ./sbin
mount --bind /sys ./sys
mount --bind /usr ./usr
mount --bind /tmp ./tmp
mount --bind /var ./var

Although they are all empty folder
I have another partition on the Flash drive too that serve as data storage

And what i'm trying to do is creating 2 partitions, one is a multiboot partition with only live Linux Distro ( Ubuntu Live, Damn small linux, dban...)  with Burg to start them  and a second partition that serve as a data storage

there is so damn little information about it, most of the guide have 3 years old, maybe there is a better alternative to burg that is as good looking as it  ?

---

