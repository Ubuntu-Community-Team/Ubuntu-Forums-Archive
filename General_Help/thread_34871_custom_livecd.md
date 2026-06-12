---
title: "custom livecd"
date: 2005-05-16
forum: General Help
---

### Post by hokim on 2005-05-16
I made my custom livecd applying these instructions to ubuntu-5.04-live-i386.iso

 [https://www.ubuntulinux.org/wiki/LiveCDCustomizationHowTo](https://www.ubuntulinux.org/wiki/LiveCDCustomizationHowTo)

I just removed all packages except packages installed by "server mode".
It works well but I can't understand the change of size.
The size of original  is 626M but that of custom is 632M.
Why does the size increase?

---

### Post by Fabien3d on 2005-05-17
I've had the same problem !

I tried to localize the livecd in french - it worked - but then, I wanted to create a mini livecd, but despite the multiple packages uninstallation, the iso image'size doesn't seem to decrease. Once, it even increased !

Fabien3D

---

### Post by britbrian on 2005-05-18
hokim

I just read the link with interest

[https://www.ubuntulinux.org/wiki/LiveCDCustomizationHowTo](https://www.ubuntulinux.org/wiki/LiveCDCustomizationHowTo)

I hope that Breezy will make it possible to make a liveCD iso directly from a real install rather than from an extracted livecd. PCLinuxOS uses a mklivecd script to do it all and is quite configurable. Just need to do df to ensure / is ~1.8GB or less before hand.

So excuse me if I'm way off base, but
1) did you bind a home user account to an automatically created user account ?.
2) & did you first clean that account of web browser caches, thumbnails, uneeded wallpapers etc, and did you have anthing mounted in that account ?.


Fabien3D

Getting it down to a miniCd is quite ambitious.
The above link mentioned that notes on removing stuff has to be expanded. IIRC the livecd also has WIndows installs for OOo, Firefox, Thunderbird & I forget what else. OOo alone compressed is 60M+. Have you removed those ?

---

### Post by hokim on 2005-05-18
Maybe you need more details about my process, because my process is not exactly same as instructions of wiki.

My process is as follows.
This is different from my first post. I added some packages to it.

> 
$mkdir mnt
$sudo mount ~/scratch/ubuntu-5.04-live-i386.iso mnt -o loop
$rsync --exclude=/casper/filesystem.cloop -a mnt/ extracted_cd
$extract_compressed_fs mnt/casper/filesystem.cloop > extracted_fs
$sudo umount mnt
$sudo mount extracted_fs mnt -o loop
$sudo mount -t proc proc mnt/proc
$sudo mount -t sysfs sysfs mnt/sys
$sudo cp /etc/apt/sources.list mnt/etc/apt/sources.list
$sudo cp /etc/resolv.conf mnt/etc
$sudo cp remove.sh mnt/root
$sudo chroot mnt/ /bin/sh
#cd root
#apt-get update
#./remove.sh
#dpkg-reconfigure locales
[quote]
en_US.UTF-8(default)
ko_KR.EUC-KR
ko_KR.UTF-8

#apt-get install xfce4
#apt-get install xfonts-base
#apt-get install xserver-xorg
#apt-get install gdm
#apt-get install ttf-unfonts
#apt-get install tcsh
#apt-get install lftp
#apt-get install mozilla-firefox
#apt-get install flashplayer-mozilla
#apt-get install nabi
#apt-get install gaim
#apt-get install gaim-guifications
#apt-get  clean
# rm /etc/resolv.conf
#exit
#chroot mnt dpkg-query -W --showformat='${Package} ${Version}\n' > extracted_cd/casper/filesystem.manifest
$sudo umount mnt/proc
$sudo umount mnt/sys
$sudo umount mnt
$sudo -s
#create_compressed_fs extracted_fs 65536 > extracted_cd/casper/filesystem.cloop
#(cd extracted_cd && find . -type f -print0 | xargs -0 md5sum > md5sum.txt)
#mkisofs -r -V "Custom Ubuntu Live CD" -cache-inodes -J -l -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o custom-hoary-live-i386.iso extracted_cd
[/quote]
I attach 'remove.sh' which make original to 'server mode'

Then I compared sizes.

ubuntu-5.04-live-i386.iso 

total size: 626M
filesystem.cloop : 497M
extracted & mounted filesystem.cloop: 1.3G

custom-hoary-live-i386.iso

total size: 736M
filesystem.cloop : 609M
extracted & mounted filesystem.cloop: 459M

---

### Post by Achille on 2005-05-29
Have you seen the explanation of Matt Zimmerman:

[http://lists.ubuntu.com/archives/ubuntu-devel/2005-May/007383.html](http://lists.ubuntu.com/archives/ubuntu-devel/2005-May/007383.html)

---

### Post by hokim on 2005-06-02
[QUOTE=Achille]Have you seen the explanation of Matt Zimmerman:

[http://lists.ubuntu.com/archives/ubuntu-devel/2005-May/007383.html](http://lists.ubuntu.com/archives/ubuntu-devel/2005-May/007383.html)[/QUOTE]

Thanks a lot :-P 

I found the solution.

This is modified process

> 
$mkdir mnt
$sudo mount ~/scratch/ubuntu-5.04-live-i386.iso mnt -o loop
$rsync --exclude=/casper/filesystem.cloop -a mnt/ extracted_cd
$extract_compressed_fs mnt/casper/filesystem.cloop > extracted_fs
$sudo umount mnt
$sudo mount extracted_fs mnt -o loop
$sudo mount -t proc proc mnt/proc
$sudo mount -t sysfs sysfs mnt/sys
$sudo cp /etc/apt/sources.list mnt/etc/apt/sources.list
$sudo cp /etc/resolv.conf mnt/etc
$sudo cp remove.sh mnt/root
$sudo chroot mnt/ /bin/sh
#cd root
#apt-get update
#./remove.sh
#./remove.sh
#./remove.sh
 
#dpkg-reconfigure locales
[quote]
en_US.UTF-8(default)
ko_KR.EUC-KR
ko_KR.UTF-8


## This is comment. A '#' means you log in with  root account.
## Until here, live cd  has packages of server installation mode without grub.
## Install your custum packages

#apt-get install xfce4
#apt-get install xfonts-base
#apt-get install xserver-xorg
#apt-get install xresprobe

## 'xresprobe' is necessary to probe X resolution.
 
#apt-get install gdm

## Before 'gdm' is installed, window manager should be intalled.

#apt-get install ttf-unfonts
#apt-get install tcsh
#apt-get install lftp
#apt-get install mozilla-firefox
#apt-get install flashplayer-mozilla
#apt-get install nabi
#apt-get install gaim
#apt-get install gaim-guifications

#apt-get  clean
# rm /etc/resolv.conf
#exit
$ sudo -s
#chroot mnt dpkg-query -W --showformat='${Package} ${Version}\n' > extracted_cd/casper/filesystem.manifest
#exit

## Sync to new filesystem image due to size problem.

$dd if=/dev/zero of=my_fs bs=65536 count=32753
$sudo losetup /dev/loop1 my_fs
$sudo mke2fs /dev/loop1
$mkdir mnt2
$sudo mount my_fs mnt2 -o loop
$sudo rsync -a mnt/ mnt2
$sudo umount mnt/proc
$sudo umount mnt/sys
$sudo umount mnt
$sudo umount mnt2

$sudo -s
#create_compressed_fs my_fs 65536 > extracted_cd/casper/filesystem.cloop
#(cd extracted_cd && find . -type f -print0 | xargs -0 md5sum > md5sum.txt)
#mkisofs -r -V "Custom Ubuntu Live CD" -cache-inodes -J -l -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o custom-hoary-live-i386.iso extracted_cd
[/quote]

One more thing.
Someone knows how to customize /install/initrd.gz(initial ramdisk)?

---

### Post by eberhardt on 2005-07-25
I'm quite new to this, but can't really figure out where the remove.sh comes from in the above.

Can anyone please explain what the remove.sh does?

---

### Post by muzzol on 2005-10-07
hi!

im already interested on creating an install cd based on ubuntu.

anyone tried?

i've readed that process is very similar to customize Live cd, but im not sure about the correct steps, so any information will be apreciated.

see you.

---

