---
title: "Error Loading Operating System"
date: 2007-12-29
forum: General Help
---

### Post by SomeStupidHippie on 2007-12-29
Hey, I just ran into this error today and I am about rip out my eyes. After fooling around a bit with GParted I can no longer boot into ubuntu, no grub, no nothing. I realize that there are a few other threads like this but none of them have been able to help me (so far)
 
Heres what happened:
Last night I thought I needed to install XP for a particular program, so i fired up GParted and went about partitioning off a bit of space off of my 10,000 RPM 74GB Raptor. All goes well, still able to boot ubuntu after it completed. Great.
So now to install XP. I get to the point where i have selected the partition to install to and it gives me the little info about how I have other operating systems installed, and how I wont be able to use those. Now, right about then I realize I can actually install the software I want to use on my Dad's computer (because I am pretty stupid sometimes)

Okay, so seeing as how there is no 'back' option, i turn off my comptuer, stick GParted back in, and grow my linux partition back to full size. This was going to take all night, so I let it be and went to sleep.
So when I wake up this morning, I find out my Dad saw GParted had finished and closed out of it, and so what I get to see very first thing is:

Error loading operating system


I can boot into a live CD and see that grub is still installed on the hard drive, or at least the folder is still there.  Everything looks okay (at least from what I can see ) in GParted too. I am greatly confused, and i really appreciate any help!

Also, if I need I need to provide any more info i would be happy too. I am running  (er.... WAS running) Gutsy gibbon. Thanks much!

---

### Post by Martin Witte on 2007-12-29
it looks like grub is there but not installed anymore, see [http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html) how to install it, you should be able to do this from the live disk

---

### Post by SomeStupidHippie on 2007-12-29
hm.... seems like I get this error just about no matter what I put in:

ubuntu@ubuntu:~$ grub-install /dev/hda
/dev/hda: Not found or not a block device


I get this no matter what....

ubuntu@ubuntu:~$ grub-install /dev/sda
/dev/sda: Not found or not a block device

ubuntu@ubuntu:~$ grub-install /dev/sda1
/dev/sda1: Not found or not a block device

ubuntu@ubuntu:~$ grub-install /dev/sd1
/dev/sd1: Not found or not a block device

ubuntu@ubuntu:~$ grub-install /dev/hd0
/dev/hd0: Not found or not a block device

ubuntu@ubuntu:~$ grub-install /dev/sd0
/dev/sd0: Not found or not a block device



I tried dragging the file from /dev into the terminal window too, still no luck


am i just doing something wrong? i feel like ive done just about everything I can....

anyway, thanks for your help

---

### Post by meierfra on 2007-12-29
grub-install  does not work from the LiveCD. 

Do analyze you problem, I  need some information.

Go to Places->Computer and double click the Ubuntu partition. (This mount your Ubuntu partition.)

Post the output of 

```
sudo fdisk -l
```

and

```
cat /media/disk/boot/grub/menu.lst
```

(all "l" are lower case L, not the number one)

---

### Post by SomeStupidHippie on 2007-12-29
When i input sudo fdisk - it tells me I am unable to open -


I assume that something is supposed to go after - but remember I am a newb so I am not exactly sure what :) Is there any way to find out?

as for the second command:

ubuntu@ubuntu:~$ cat /media/disk/boot/grub/menu.lst
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
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=b855572f-5f5d-4672-97d1-2a2495f646f4 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b855572f-5f5d-4672-97d1-2a2495f646f4 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b855572f-5f5d-4672-97d1-2a2495f646f4 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by meierfra on 2007-12-29
Sorry, I had a typo. it should be

```
sudo fdisk -l
```

---

### Post by SomeStupidHippie on 2007-12-29
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b3b33

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8666    69609613+  83  Linux
/dev/sda3            8667        9039     2996122+   5  Extended
/dev/sda5            8667        9039     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00099aa2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19452   156248158+  83  Linux

---

### Post by meierfra on 2007-12-29
This should work:

```
sudo grub
```

and at the grub prompt:


```
root (hd0,0)
setup (hd0)
quit
```

---

### Post by SomeStupidHippie on 2007-12-29
Thanks so much! That did the trick! Feels great to have my OS back, heh

---

