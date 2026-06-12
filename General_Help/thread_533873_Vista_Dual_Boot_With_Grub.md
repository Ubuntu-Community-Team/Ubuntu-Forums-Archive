---
title: "Vista Dual Boot With Grub"
date: 2007-08-24
forum: General Help
---

### Post by larker on 2007-08-24
I decided I would give Ubuntu a try and so last night I burned myself a copy of Ubuntu 7.04 Feisty. I've been working on a computer dual booted for XP (original OS) and Vista (partitioned onto the second half of the same drive). Today, I loaded up the Ubuntu CD and used Gparted to clear out the half of the drive with XP on it. I installed Ubuntu without any problems and have set up grub to load up with the following menu.lst:

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		30

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)

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
# kopt=root=UUID=c855c6ad-c254-4251-a1b3-cc86b3f14269 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=c855c6ad-c254-4251-a1b3-cc86b3f14269 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=c855c6ad-c254-4251-a1b3-cc86b3f14269 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=c855c6ad-c254-4251-a1b3-cc86b3f14269 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=c855c6ad-c254-4251-a1b3-cc86b3f14269 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

title Vista
rootnoverify (hd0,4)
savedefault
make active
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Every time I load up into the grub menu, however, I get the 4 Ubuntu options and the memory check option. I also have the Vista option I set up there but it does not work. Either it'll say "A disk read error occurred" with ctrl+alt+del for restart or that it can't find the drive or device. I also got it (with a slightly different menu.lst file) to say "Starting up..." but then it hangs and goes nowhere.

My Gparted shows that I've got the Vista install on /dev/sda/5 as the partition and /media/sda5 as the mountpoint. I'm very new (as in 100% n00b) with Linux and I really would appreciate some help. I'm hoping I don't have to reinstall Vista since I've got it set up quite nicely for all the things I usually do on my PC. Please help me out.

---

### Post by MoLE on 2007-09-02
Hi, and welcome to Ubuntu.

You might want to have a look at the following pages which describe the process nicely.

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)
[http://apcmag.com/3895/how_vista_screws_dual_booting_nirvana](http://apcmag.com/3895/how_vista_screws_dual_booting_nirvana)
[http://ubuntuforums.org/showthread.php?t=207870](http://ubuntuforums.org/showthread.php?t=207870)


You may may have more luck with responses in the Installation or Absolute Beginner forums.

---

### Post by MoLE on 2007-09-02
Another link you may find helpful.

[http://sathyasays.wordpress.com/2007/06/12/vista-ubuntu-dual-boot/](http://sathyasays.wordpress.com/2007/06/12/vista-ubuntu-dual-boot/)

---

### Post by Nathan_M on 2007-09-02
Yet another... one of my own:

[http://ubuntuforums.org/showthread.php?t=426334](http://ubuntuforums.org/showthread.php?t=426334)

I wrote it when I first installed ubuntu. I was completely new to it all, so the instructions are pretty basic. If you need to start again with your ubuntu install, I recommend following these instructions (although you've already got the partition set up, so you don't need to do the Vista bit).

---

### Post by Irihapeti on 2007-09-02
I seem to recall reading somewhere that Vista (or any windows) needs to be on the first partition, which would be /sda1 in your case (I presume).

---

### Post by Pharisee on 2007-09-03
I recieved that "A disk read error occurred" after I allowed a Linux distro to resize my Vista partition. I found out later that the NTFS that Vista uses is different than that of XP any Linux app meddling with it destroys it :(

If you touched your Vista installation at all , then that may be the reason you're having isssues.

---

### Post by eggdeng on 2007-09-03
The menu.lst file is badly edited. The Vista entry should go after the line > ### END DEBIAN AUTOMAGIC KERNELS LISTand read (if your Vista is on sda5):

```
title		Vista
root		(hd0,4)
chainloader	 +1
```

---

