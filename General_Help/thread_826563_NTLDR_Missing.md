---
title: "NTLDR Missing"
date: 2008-06-12
forum: General Help
---

### Post by subzero22 on 2008-06-12
My Win XP Home Edition was ok but then I got Win XP Pro and I ended up reformatting the drive. Now I was able to get into xp just fine but since I installed it Grub didn't work.

Now I got Grub to work but my XP won't load up and keeps saying NTLDR is missing. I can load into Ubuntu Linux just fine.

I've tried for about 2 hours now searching online and in these forums and can't find anything to fix it. I was wondering if someone can help. I have 2 hard drives and when I tried to fix grub the first time I used the code setup (hd1) and since that didn't work I did it again but this time using setup (hd0). I ended up getting grub working.

Is there anyway I can get my NTLDR working again? I'm not sure if it's the version of windows changed or if me doing the hd1 that messed it up or if it's something else.

I got Windows set up in my second hard drive wich would be hd1,0.

I know the menu.lst is kinda long so I won't post it unless someone asks. I just need to get my ntldr working again.

---

### Post by darco on 2008-06-12
Have you tried running the repair option from the Windows CD? Theres also SuperGrub utility disk that you can look into.

good luck
darco

---

### Post by cariboo on 2008-06-12
THe reason NTLDR is missing is that Windows wants to boot off of the first hard drive, by installing Unbuntu on the first hard drive you overwrote the windows boot files. You may be able to repair this  if you go into the repair console in windows XP and copy the appropriate files to the hdd Windows is on.

Jim

---

### Post by subzero22 on 2008-06-12
> Have you tried running the repair option from the Windows CD? Theres also SuperGrub utility disk that you can look into.

yes I've tried running the repair option and can get windows to work but then it takes grub off for some reason or other. Unless I'm doing something wrong.

> THe reason NTLDR is missing is that Windows wants to boot off of the first hard drive, by installing Unbuntu on the first hard drive you overwrote the windows boot files. You may be able to repair this if you go into the repair console in windows XP and copy the appropriate files to the hdd Windows is on.

Accually there's nothing but storage files on the first hard drive. And My first windows when I had the home edition installed didn't have no problem with it as long as it was in front of the drive. 

I've always had windows on my sata drive but when I put in a storage drive wich is an ata hard drive. My sata drive which came with the computer became the second hard drive for some reason or another.

EDIT: Oh ya Ubuntu is also on my sata drive or second hard drive. It's like 2 partitions down from windows.

Thanks for the fast replies

---

### Post by meierfra. on 2008-06-12
Please post the output of 

```
sudo fdisk -l
```

and

```
cat /boot/grub/menu.lst
```
(both "l" are lowercase L"

so that we can see whether grub is configured correctly.

From you description it seems that


```
title XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1
```

should be the correct item for Windows. But I won't be able to tell for sure until I see "fdisk" and "menu.lst"

---

### Post by meierfra. on 2008-06-12
> THe reason NTLDR is missing is that Windows wants to boot off of the first hard drive, by installing Unbuntu on the first hard drive you overwrote the windows boot files

Ubuntu does no overwrite any Windows boot files unless you either delete a partition which contained  the boot files or you install grub to the boot sector of a windows partition.( But in the latter case one would not get an "NTLDR" missing message)

Most often "NTLDR missing" does not mean that "NTLDR" is actually missing, but only that Grub is looking at the wrong place.

---

### Post by subzero22 on 2008-06-12
here's the fdisk

```
Disk /dev/hdc: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xdea8ddce

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       10337    78147688+   7  HPFS/NTFS

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbac79d93

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9053    72712048+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            9053       14152    40963860    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           14153       24321    81682020    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda5           14153       14917     6144831   82  Linux swap / Solaris
/dev/sda6           14918       24321    75531928+  83  Linux

```

And here's the menu.lst

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=3cb07210-ab92-4f7c-9378-2ea1e7280d24 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,5)

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
root            (hd1,5)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3cb07210-ab92-4f7c-9378-2ea1e7280d24 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,5)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3cb07210-ab92-4f7c-9378-2ea1e7280d24 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,5)
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
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

---

### Post by meierfra. on 2008-06-12
Go  to "Places->Computer" and look at all  three NTFS partition and see whether any of them has the "NTLDR" file (it would be in the top folder , so you should see it immediately after Double clicking  the icon for the partition.


Try 

title           Microsoft Windows XP Home Edition
root            (hd1,1)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1



and

title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

(you can put  both of them on menu.lst at the same time)


Did you deleted any partition while installing Ubuntu?

---

### Post by subzero22 on 2008-06-12
it's in the hdc1 wich I think is kinda weird as window's isn't installed there lol.

No I didn't install ubuntu. all I did was delete windows and reinstalled it. Then I re-installed grub using the sudo grub ect ect.

Ok now I can edit the menu.lst but it won't let me save it. how do I change it to hd0,0 ??

---

### Post by meierfra. on 2008-06-12
> but it won't let me save it

Open menu.lst with 

```
gksudo gedit /boot/grub/menu.lst
```

> it's in the hdc1 


then 

title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1

should work

---

### Post by subzero22 on 2008-06-12
Thanks for all the help you gave me. I got it working.

---

### Post by meierfra. on 2008-06-12
> it's in the hdc1 wich I think is kinda weird as window's isn't installed there 
Windows always puts all the  boot  information on one fixed primary (NTFS or Fat) partition on the FIRST hard drive. (This is due to the way the Windows Boot Loader works)

Since the bios are set to boot from /dev/hdc1, Windows put  the boot information on /dev/hdc1.


> You may be able to repair this if you go into the repair console in windows XP and copy the appropriate files to the hdd Windows is on.

This would have worked,too. Actually one could have just copied the files "boot.ini", "NTLDR" and "ntdetect.com " from hdc1 to  sda1 and  edit boot.ini. After that "root (hd1,0)" would have worked.

---

### Post by subzero22 on 2008-06-12
oh cool. That's good to know for future reference.

---

