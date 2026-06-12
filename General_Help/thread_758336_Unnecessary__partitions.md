---
title: "Unnecessary  partitions"
date: 2008-04-17
forum: General Help
---

### Post by penguin5 on 2008-04-17
This is how my hard drive looks like:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1        87168690    89851544     1341427+  27  Unknown
/dev/sda2        89851545   234436544    72292500    5  Extended
/dev/sda3   *    15326010    87168689    35921340    7  HPFS/NTFS
/dev/sda4              63    15326009     7662973+   7  HPFS/NTFS
/dev/sda5       225375948   234436544     4530298+  82  Linux swap / Solaris
/dev/sda6        89851671   219753134    64950732   83  Linux
/dev/sda7       219753198   225375884     2811343+  82  Linux swap / Solaris

Im dual booting vista with ubuntu. For some reason I have 2 swap partitions and little 1.4GB partiton that I have no idea is for. How do I get rid of them? I dont wish to delete anything that may cause a GRUB error but I dont what these pointless partitions. Any suggestions?

---

### Post by Aifel on 2008-04-17
> **penguin5 said:**
> This is how my hard drive looks like:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1        87168690    89851544     1341427+  27  Unknown
/dev/sda2        89851545   234436544    72292500    5  Extended
/dev/sda3   *    15326010    87168689    35921340    7  HPFS/NTFS
/dev/sda4              63    15326009     7662973+   7  HPFS/NTFS
/dev/sda5       225375948   234436544     4530298+  82  Linux swap / Solaris
/dev/sda6        89851671   219753134    64950732   83  Linux
/dev/sda7       219753198   225375884     2811343+  82  Linux swap / Solaris

Im dual booting vista with ubuntu. For some reason I have 2 swap partitions and little 1.4GB partiton that I have no idea is for. How do I get rid of them? I dont wish to delete anything that may cause a GRUB error but I dont what these pointless partitions. Any suggestions?

Most likely GRUB is on your MBR, so as long as you don't go deleting your Windows (or /dev/sda3 I believe) partitions you'll be fine.

If you want to go modify/delete your partitions, you can install gparted (sudo apt-get install gparted). 

In gparted, one of your swap partitions will be already in use. Delete the one that's not in use.

As for your mysterious 1.4 GB partition... I have no idea. :(

---

### Post by sekinto on 2008-04-17
Open up a terminal:
```
sudo fdisk /dev/<drive>
d
<partition #>
```

<drive> is your hard drive (example: hda, sda, hdb, et cetera).
<partition> is the partition you want to delete (1, 2, 3, 4, et cetera).

---

### Post by penguin5 on 2008-04-18
NO! I deleted the swap file and the small partition and now I have GRUB ERROR 17.

This is my HDD now:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda2        89851545   234436544    72292500    5  Extended
/dev/sda3   *    15326010    89851544    37262767+   7  HPFS/NTFS
/dev/sda4              63    15326009     7662973+   7  HPFS/NTFS
/dev/sda5        89851608   231705494    70926943+  83  Linux
/dev/sda6       231705558   234436544     1365493+  82  Linux swap / Solaris

Please advice on what to do

Thanks

---

### Post by sekinto on 2008-04-18
What purpose did the small partition play?

Also could you post the output of "sudo cat /boot/grub/grub.conf"?

---

### Post by penguin5 on 2008-04-18
> **sekinto said:**
> What purpose did the small partition play?

Also could you post the output of "sudo cat /boot/grub/grub.conf"?

Im not sure what the small partition was for but I believe it was empty. I just merged it witht he NFTS partition with my vista. As for the output you asked for:

ubuntu@ubuntu:~$ sudo cat /boot/grub/grub.conf
cat: /boot/grub/grub.conf: No such file or directory

I got this through the ubuntu live CD so maybe thats why it cant find it.

---

### Post by sekinto on 2008-04-18
Ah, if you are on the live CD you have to do this:

sudo cat /media/<UBUNTU-MOUNT>/boot/grub/grub.conf

<UBUNTU-MOUNT> == Whatever directory your Ubuntu partition is mounted in.

---

### Post by penguin5 on 2008-04-18
> **sekinto said:**
> Ah, if you are on the live CD you have to do this:

sudo cat /media/<UBUNTU-MOUNT>/boot/grub/grub.conf

<UBUNTU-MOUNT> == Whatever directory your Ubuntu partition is mounted in.

Sorry Im not very experienced with this, does ubuntu mount mean that number that comes with sda#? I think its sda5 but it doesnt work. Also, my gparted says that my ubuntu partition is not mounted and I cant mount it. Same with my other vista partition. Thanks for helping me out.

---

### Post by sekinto on 2008-04-18
Then you will have to mount it. Open gParted, find the Ubuntu partition, then you right click on it or something like that and there should be a mount option.

---

### Post by penguin5 on 2008-04-18
I mounted them, although not through gparted. But the command will now work, keeps giving me command not found. What do I type in for my ubuntu partion(ubuntu mount) Im not sure.

---

### Post by sekinto on 2008-04-18
can you post the output of "ls /media", because it is one of the directories in your media folder most likely.

---

### Post by penguin5 on 2008-04-18
> **sekinto said:**
> can you post the output of "ls /media", because it is one of the directories in your media folder most likely.

Im really sorry but im not sure what you mean. What do I type into the terminal? Sorry for stupid questions. How do i find the output?

---

### Post by sekinto on 2008-04-18
Type
```
ls /media
```
in the terminal.

It will tell you all the directories in your media folder, one is probably for Ubuntu.

Or you could also just navigate to /media in Nautilus and find it.

---

### Post by penguin5 on 2008-04-18
> **sekinto said:**
> Type
```
ls /media
```
in the terminal.

It will tell you all the directories in your media folder, one is probably for Ubuntu.

Or you could also just navigate to /media in Nautilus and find it.

ACER  disk  disk-1

---

### Post by sekinto on 2008-04-18
Open up nautilus and see which one is your Ubuntu partition. Your Ubuntu partion will have folders like home, var, tmp, root, et cetera...

---

### Post by penguin5 on 2008-04-18
> **sekinto said:**
> Open up nautilus and see which one is your Ubuntu partition. Your Ubuntu partion will have folders like home, var, tmp, root, et cetera...

My ubuntu is in 72.6GB partition. Im not sure what exactly you need out of that. In gparted its under /media/disk mount point and dev/sda5 for ubuntu and for extended that holds ubuntu and swap its dev/sda2

---

### Post by sekinto on 2008-04-18
Okay, what is the output of:
```
sudo cat /media/disk/boot/grub/grub.conf
```

---

### Post by penguin5 on 2008-04-18
> **sekinto said:**
> Okay, what is the output of:
```
sudo cat /media/disk/boot/grub/grub.conf
```

ubuntu@ubuntu:~$ sudo cat /media/disk/boot/grub/grub.conf
cat: /media/disk/boot/grub/grub.conf: No such file or directory

Do you think the problem might have been that the partitions hove not been mounted? Its just that if I restart ill have to wait forever to load the internet back up through this live CD.

---

### Post by sekinto on 2008-04-18
What does 
```
ls /media/disk/boot/grub
```
put out?

---

### Post by penguin5 on 2008-04-18
ubuntu@ubuntu:~$ ls /media/disk/boot/grub
default        fat_stage1_5       menu.lst           stage1
device.map     installed-version  minix_stage1_5     stage2
e2fs_stage1_5  jfs_stage1_5       reiserfs_stage1_5  xfs_stage1_5
ubuntu@ubuntu:~$

---

### Post by sekinto on 2008-04-18
Ah, I gave you the wrong file, sorry about that.
```
sudo cat /media/disk/boot/grub/menu.lst
```

---

### Post by penguin5 on 2008-04-18
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# kopt=root=UUID=5b79fa73-2411-49d4-b3b3-0dbfb843cabf ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=5b79fa73-2411-49d4-b3b3-0dbfb843cabf ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=5b79fa73-2411-49d4-b3b3-0dbfb843cabf ro single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu hardy (development branch), memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Windows NT/2000/XP
root		(hd0,3)
savedefault
makeactive
chainloader	+1

---

### Post by sekinto on 2008-04-18
Does this "error 17" appear before the Grub menu can load, or does it happen after a choice is selected?

---

### Post by penguin5 on 2008-04-18
the error 17 appears before the menu. I cant even get to the menu.

---

### Post by sekinto on 2008-04-18
Try installing Grub again and restarting. You can do this easily:
```
sudo grub
root (hdX,Y)
setup (hdX)
exit
```

X == # of your hard drive - 1
Y == # of partition - 1

So if your Ubuntu partition is the third partition on your second hard drive
x == 2 - 1
x == 1
Y == 3 - 1
Y == 2

So just replace X and Y with your hard drive and partition numbers.
The # of your partition corresponds to where it is in your partitioning layout.

---

### Post by penguin5 on 2008-04-18
Actually I cant get to that menu by pressing c. I will not let me .l

---

### Post by sekinto on 2008-04-18
What do you mean?

---

### Post by penguin5 on 2008-04-18
when Im given the error GRUB 17, where do i type in the code to reinstall grub?

---

### Post by sekinto on 2008-04-18
You just do that from a terminal on the live CD.

---

### Post by penguin5 on 2008-04-18
> **sekinto said:**
> Try installing Grub again and restarting. You can do this easily:
```
sudo grub
root (hdX,Y)
setup (hdX)
exit
```

X == # of your hard drive - 1
Y == # of partition - 1

So if your Ubuntu partition is the third partition on your second hard drive
x == 2 - 1
x == 1
Y == 3 - 1
Y == 2

So just replace X and Y with your hard drive and partition numbers.
The # of your partition corresponds to where it is in your partitioning layout.

what do you mean by x==2 - 1 ? I have to subtract by 1? Please explain if possible

---

