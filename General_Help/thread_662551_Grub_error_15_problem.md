---
title: "Grub error 15 problem"
date: 2008-01-09
forum: General Help
---

### Post by MoHamm on 2008-01-09
Hi All

I am getting "Grub error 15" on boot and get only a black screen. I am now loading from cd.
It seems that grub is attempting to boot from the wrong partition.

This is the output of fdisk -l from live cd.

 >   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         653     5245191   12  Compaq diagnostics
/dev/sda2   *         654        3284    21133507+   7  HPFS/NTFS
/dev/sda3            3285        4500     9767520   83  Linux
/dev/sda4            4501       14593    81072022+   f  W95 Ext'd (LBA)
/dev/sda5            5306        6531     9847813+   b  W95 FAT32
/dev/sda6            6532        9291    22169668+   b  W95 FAT32
/dev/sda7            9292        9795     4048348+  82  Linux swap / Solaris
/dev/sda8            9796       14593    38539903+   b  W95 FAT32
/dev/sda9            4501        5305     6466099+  83  Linux


If I am right and I need to change the boot back to /dev/sda3 which is the linux partition then how to do so is the question..

Thanks in advance.
Peace 
Mo

---

### Post by meindian523 on 2008-01-09
Please post /boot/grub/menu.lst

---

### Post by MoHamm on 2008-01-09
Can you please tell me how to access it from ubuntu live cd. This has been my obstacle.

---

### Post by meindian523 on 2008-01-09
Open Terminal.
```
sudo fdisk -l
```
```
sudo -i
```
```
mkdir /mnt/a
```
```

mount /dev/sda3 /mnt/a
```
or```

mount /dev/sda9 /mnt/a
```

depending on whether your sda3 is the / partition or sda9 is your / partition.

Basically we are mounting your / partition on a directory we created in /mnt called "a".Now,just

```
chroot /mnt/a
```

and then you can do```
nautilus
``` and post /boot/grub/menu.lst

---

### Post by MoHamm on 2008-01-09
so at least now I know i been doing it right.

I have been mounting it since yesterday but all I get is a lost and found directory, in it is the following:

> total 676
drwx------  40 root root   4096 2008-01-07 21:30 .
drwxr-xr-x   3 root root   4096 2008-01-07 21:30 ..
drwxr-xr-x   4 root root   4096 2007-10-15 23:28 #1042433
drwxr-xr-x   3 root root   4096 2008-01-04 15:24 #130305
drwxr-xr-x   2 root root   4096 2008-01-04 15:23 #211745
drwxr-xr-x   2 root root   4096 2007-10-15 23:17 #244321
drwxr-xr-x   2 root root   4096 2008-01-07 21:25 #276897
drwxr-xr-x   2 root root   4096 2008-01-04 15:26 #276898
-rw-r--r--   1 root root   2227 2007-05-15 16:07 #276899
-rw-r--r--   1 root root    141 2007-05-15 16:07 #276900
drwx------   3 root root   4096 2008-01-07 20:05 #281463
-rw-------   1 root root     61 2008-01-07 21:25 #281527
drwx------   5 root root   4096 2008-01-06 14:32 #281528
drwx------   2 root root   4096 2008-01-04 11:32 #281529
drwx------   3 root root   4096 2008-01-07 20:06 #281531
drwx------   2 root root   4096 2008-01-07 20:07 #281532
-rw-r--r--   1 root root   2019 2008-01-06 14:32 #284059
lrwxrwxrwx   1 root root     27 2008-01-07 15:05 #284084 -> libgmodule-2.0.so.0.1200.13
lrwxrwxrwx   1 root root     27 2008-01-07 15:05 #284085 -> libgmodule-2.0.so.0.1200.13
-rwxr-xr-x   1 root root    871 2008-01-07 15:05 #284086
-rwxr-xr-x   1 root root  34276 2008-01-07 15:05 #284087
lrwxrwxrwx   1 root root     27 2008-01-07 15:05 #284088 -> libgthread-2.0.so.0.1200.13
lrwxrwxrwx   1 root root     27 2008-01-07 15:05 #284089 -> libgthread-2.0.so.0.1200.13
-rwxr-xr-x   1 root root    881 2008-01-07 15:05 #284090
-rwxr-xr-x   1 root root 180664 2008-01-07 15:03 #284091
lrwxrwxrwx   1 root root     18 2008-01-07 15:03 #284092 -> libvorbis.so.0.4.0
lrwxrwxrwx   1 root root     18 2008-01-07 15:03 #284093 -> libvorbis.so.0.4.0
-rwxr-xr-x   1 root root    868 2008-01-07 15:03 #284094
-rwxr-xr-x   1 root root  37164 2008-01-07 15:03 #284095
-rw-r--r--   1 root root 191286 2008-01-07 15:03 #284096
drwx------   2 root root   4096 2008-01-04 16:06 #297411
drwxr-xr-x   2 root root   4096 2008-01-04 18:02 #298810
drwxr-xr-x   3 root root   4096 2008-01-05 16:57 #298855
drwxr-xr-x  13 root root   4096 2008-01-04 16:04 #32577
drwxr-xr-x   2 root root   4096 2008-01-05 16:57 #325945
drwx------   4 root root   4096 2008-01-05 16:57 #331406
drwxr-xr-x   3 root root   4096 2008-01-05 16:57 #331425
drwxr-xr-x   2 root root   4096 2007-10-15 23:17 #390913
drwxr-xr-x   2 root root   4096 2008-01-07 21:24 #428951
drwxr-xr-x   2 root root   4096 2008-01-07 21:24 #428999
drwxr-xr-x   2 root root   4096 2008-01-07 21:24 #429000
drwxr-xr-x   2 root root   4096 2008-01-07 21:24 #429001
drwxr-xr-x   2 root root   4096 2008-01-07 21:24 #429002
drwxr-xr-x   2 root root   4096 2008-01-07 21:24 #429003
drwxr-xr-x   2 root root   4096 2008-01-07 21:24 #429004
drwxr-xr-x   2 root root   4096 2008-01-06 17:53 #439873
drwxr-xr-x   2 root root   4096 2008-01-04 12:16 #456065
lrwxrwxrwx   1 root root     11 2008-01-04 12:16 #48865 -> media/cdrom
drwxr-xr-x  18 root root  12288 2008-01-04 17:44 #553793
drwxr-xr-x  11 root root   4096 2008-01-07 21:25 #586369
drwxr-xr-x   2 root root   4096 2007-10-15 23:17 #65153
drwxr-xr-x 134 root root  12288 2008-01-07 21:28 #765537
drwxr-xr-x   2 root root   4096 2007-10-04 11:17 #781825
drwxr-xr-x   2 root root   4096 2007-10-08 10:47 #798113
drwxrwxrwt   4 root root   4096 2008-01-07 21:27 #81441
-rw-r--r--   1 1000 1000   1773 2007-12-17 06:50 #81704
-rw-r--r--   1 1000 1000  15140 2007-12-17 06:50 #82137
drwxr-xr-x   2 root root   4096 2008-01-04 12:40 #846977
lrwxrwxrwx   1 root root     33 2008-01-04 12:39 #84925 -> boot/initrd.img-2.6.22-14-generic
lrwxrwxrwx   1 root root     30 2008-01-04 12:39 #84926 -> boot/vmlinuz-2.6.22-14-generic
drwxr-xr-x  15 root root   4096 2007-10-15 23:31 #928417
drwxr-xr-x   2 root root   4096 2007-10-08 10:47 #993569

hope this helps.
thanks a lot

---

### Post by MoHamm on 2008-01-09
... and this is the output of chroot /mnt/a
> 
chroot: cannot run command `/bin/bash': No such file or directory

---

### Post by meindian523 on 2008-01-09
What you posted is a ls -l
Post the contents of the file menu.lst in /boot/grub,it's a text file.

If that's the error of chroot,it means you have mounted the wrong partition to /mnt/a,try the other partition that is if you mounted /dev/sda3 now,umount it and mount /dev/sda9 and vice versa.

---

### Post by MoHamm on 2008-01-09
ok so, /dev/sda3 is / and /dev/sda9 is /home

all the steps were done as mentioned above but still getting the same output, 
could it be that the / partition is damaged and thats non of its contents are visible when it is mounted? 
what can the contents of the lost and found directory be?

thanks again

---

### Post by meindian523 on 2008-01-09
I don't think you followed the instructions since the output is of a list files while the expectation is a text file like this:

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
default 4

splashimage=(hd0,4)/grub/mac4grub/mac05.xpm.gz

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/white/blue

#splashimage=(hd0,8)/grub/splashimage.xpm.gz
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
# kopt=root=UUID=7cd4e9af-3c08-4391-8125-8b1b3a503207 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,8)

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

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,4)
kernel          /vmlinuz-2.6.20-16-generic root=UUID=7cd4e9af-3c08-4391-8125-8b1b3a503207 ro quiet splash
initrd          /initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,4)
kernel          /vmlinuz-2.6.20-16-generic root=UUID=7cd4e9af-3c08-4391-8125-8b1b3a503207 ro single
initrd          /initrd.img-2.6.20-16-generic

#title          Ubuntu, kernel 2.6.20-15-generic
#root           (hd0,4)
#kernel         /vmlinuz-2.6.20-15-generic root=UUID=7cd4e9af-3c08-4391-8125-8b1b3a503207 ro quiet splash
#initrd         /initrd.img-2.6.20-15-generic
#quiet
#savedefault

#title          Ubuntu, kernel 2.6.20-15-generic (recovery mode)
#root           (hd0,4)
#kernel         /vmlinuz-2.6.20-15-generic root=UUID=7cd4e9af-3c08-4391-8125-8b1b3a503207 ro single
#initrd         /initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,4)
kernel          /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title   Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

---

### Post by MoHamm on 2008-01-09
Ok I managed to find grub/menu.lst in the #130305 file in the lost and found
here it is:

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
# kopt=root=UUID=b478edd2-2bf2-40f4-9938-972f324b57f7 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b478edd2-2bf2-40f4-9938-972f324b57f7 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b478edd2-2bf2-40f4-9938-972f324b57f7 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


cheers

---

### Post by meindian523 on 2008-01-09
1]Move the menu.lst file to /boot/grub from the lost+found.
2]There's no problem with your menu.lst.

Just as a insurance,logout of the chroot environment,now you will be at a ubuntu@ubuntu:~:# kind of prompt,type ```
blkid /dev/sda9
``` and copy the UUID="......." to replace the [COLOR="Red"]red[/COLOR] text in the code below IF they are different.
 ```
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=[COLOR=Red]b478edd2-2bf2-40f4-9938-972f324b57f7[/COLOR] ro quiet splash
```

---

### Post by MoHamm on 2008-01-09
I cant seem to locate boot/grub 

what should the output of blkid /dev/sda9 be cause i am not getting anything

---

### Post by meindian523 on 2008-01-09
```
easwarh@l1nuxr0cks:~$ blkid /dev/hda8
/dev/hda8: UUID="245282ca-f597-424c-b182-84ceb228cd2e" SEC_TYPE="ext2" TYPE="ext3" 
easwarh@l1nuxr0cks:~$ 

```

Something like this.
Not boot/grub,find **[COLOR="Red"]/[/COLOR]**boot/grub,and be careful that you are in the chrooted environment when you replace the line.

---

### Post by MoHamm on 2008-01-09
Thanks for all.. I know I am tiring you with this issue but I will post everything i am doing from the beginning to make sure i am following the instructions properly.



> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaebca75d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         653     5245191   12  Compaq diagnostics
/dev/sda2   *         654        3284    21133507+   7  HPFS/NTFS
/dev/sda3            3285        4500     9767520   83  Linux
/dev/sda4            4501       14593    81072022+   f  W95 Ext'd (LBA)
/dev/sda5            5306        6531     9847813+   b  W95 FAT32
/dev/sda6            6532        9291    22169668+   b  W95 FAT32
/dev/sda7            9292        9795     4048348+  82  Linux swap / Solaris
/dev/sda8            9796       14593    38539903+   b  W95 FAT32
/dev/sda9            4501        5305     6466099+  83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# mkdir /mnt/a
root@ubuntu:~# mount /dev/sda3 /mnt/a/
root@ubuntu:~# chroot /mnt/a/
chroot: cannot run command `/bin/bash': No such file or directory


I then cd the mounted partition /dev/sda3 which is root

> root@ubuntu:~# cd /mnt/a
root@ubuntu:/mnt/a# ls
lost+found


I think this is where i should be able to see /boot , right??

as I mentioned earlier I was able to locate /grub/menu.lst in the lost and found;

 > root@ubuntu:/mnt/a# cd lost+found/
root@ubuntu:/mnt/a/lost+found# ls 
#1042433  #281463  #284085  #284093  #325945  #429002  #65153   #84925
#130305   #281527  #284086  #284094  #331406  #429003  #765537  #84926
#211745   #281528  #284087  #284095  #331425  #429004  #781825  #928417
#244321   #281529  #284088  #284096  #390913  #439873  #798113  #993569
#276897   #281531  #284089  #297411  #428951  #456065  #81441
#276898   #281532  #284090  #298810  #428999  #48865   #81704
#276899   #284059  #284091  #298855  #429000  #553793  #82137
#276900   #284084  #284092  #32577   #429001  #586369  #846977
root@ubuntu:/mnt/a/lost+found# cd \#130305/
root@ubuntu:/mnt/a/lost+found/#130305# ls
abi-2.6.22-14-generic         initrd.img-2.6.22-14-generic.bak
config-2.6.22-14-generic      memtest86+.bin
grub                          System.map-2.6.22-14-generic
initrd.img-2.6.22-14-generic  vmlinuz-2.6.22-14-generic
root@ubuntu:/mnt/a/lost+found/#130305# cd grub/
root@ubuntu:/mnt/a/lost+found/#130305/grub# ls
default        installed-version  minix_stage1_5     xfs_stage1_5
device.map     jfs_stage1_5       reiserfs_stage1_5
e2fs_stage1_5  menu.lst           stage1
fat_stage1_5   menu.lst~          stage2


but I am not able to copy it to the /boot/grub cause I can not locate it, am I missing something here?

> Just as a insurance,logout of the chroot environment,now you will be at a ubuntu@ubuntu:~:# kind of prompt,type
Code:

blkid /dev/sda9

and copy the UUID="......." to replace the red text in the code below IF they are different.
Code:

kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=b478edd2-2bf2-40f4-9938-972f324b57f7 ro quiet splash


I think I just messed up, I did the following while in root and got this output;

> root@ubuntu:~# blkid /dev/sda9
/dev/sda9: UUID="bc34b58e-37b7-45fe-a53f-cf0bd7dd3ece" SEC_TYPE="ext2" TYPE="ext3" 

---

### Post by meindian523 on 2008-01-09
hum,I'm sorry,I misunderstood.

Your entire / is in the lost+found,you will have to restore all the files recreating all the folders if necessary.That's why chroot failed because even your /etc,/bin,etc are in the lost+found.This is something major,any idea what you did before this happened?

In hindsight,it's better you posted the results of each step.

---

### Post by MoHamm on 2008-01-09
no worries... 

last I was doing was compiling packages, so i did a lot of new installations relating to a video editing application. the last applications I recall I installed were gtk and alsa, after that when I rebooted the system would hang after the login page, so I went into text mode and I fsck'd the / partition, It was mounted. It then asked me to reboot and thats when I started getting the error 15 at Grub.

Is it possible to restore all the files from lost and found or should i just opt for a clean re-install?
I would like to give restoring a if it wont be too time consuming.

thanks again

---

### Post by meindian523 on 2008-01-09
Ah,you fscked the / partition while it was mounted?It usually gives a warning of possibility of severe damage in that case.

Well,looking at your ls,it looks that you CAN restore them back,depends on how much time you got.

Pros:
1]You get a crash course in Linux filesystem structure absolutely free!
2]The main directories like /etc,/bin,etc. have moved to lost+found BUT with their subdirectories INSIDE them,that's good news.

Cons:
1]You will have to look at the contents of each directory and realise where in the filesystem it should go(basically what name it should have /<what?>,got it?)


So,if you have about 45 mins to an hour to spare,you can do the moving,while a reinstall takes about 30 mins,but you will have to reinstall all your apps(whether compiled or otherwise) and there's no predicting how much time that can take.So,make your call and post back.

---

### Post by meindian523 on 2008-01-09
A thanks would be more effective if it was recorded with the forums. Just a thought......

---

### Post by MoHamm on 2008-01-09
hey..


> 1]You will have to look at the contents of each directory and realise where in the filesystem it should go(basically what name it should have /<what?>,got it?)

and then what do i do? how do I place it where it should be?



> So,if you have about 45 mins to an hour to spare,you can do the moving,while a reinstall takes about 30 mins
45-60 minutes too good to be true.
I cant think of a better way than to spend my bday gettting my linux back up. I have however mastered the re-installation

> A thanks would be more effective if it was recorded with the forums. Just a thought...... 

trying to find out how


ALSO if I were to re-install do I risk losing all the data on all my partitions because of the error 15 is in the /boot/grub.. I'm worried

---

### Post by meindian523 on 2008-01-10
> **MoHamm said:**
> hey..

45-60 minutes too good to be true.
I cant think of a better way than to spend my bday gettting my linux back up. I have however mastered the re-installation

Happy Birthday!BTW,Is that sarcasm?
> **MoHamm said:**
> 

ALSO if I were to re-install do I risk losing all the data on all my partitions because of the error 15 is in the /boot/grub.. I'm worried
Depends on whether you have a separate /home partition or not,if not,reinstall will result in loss of data but not if you have a separate /home partition(in case you do have a /home partition,you just opt out of formatting your /home partition during reinstall)

If you are planning to move the stuff back to it's place,then this graphic will do some good.About your question how you will find out where to place them,a factor in your favour is that all the sub-directories are still within their parent directories,so you just move all of them to /.

---

### Post by meindian523 on 2008-01-10
And about how to record your thanks,just click the "Star with a blue ribbon" button next to the post(and poster) you want to thank.

---

### Post by meindian523 on 2008-01-10
[QUOTE="MoHamm"]I have however mastered the re-installation[/QUOTE]

Does that mean:
1]You have a image of your linux partition stored somewhere so you can restore it.

or

2]You are comfortable with reinstalling because you don't feel it's hard?

---

### Post by MoHamm on 2008-01-10
> Happy Birthday!BTW,Is that sarcasm?

Thanks. It was. There is sarcasm in that statement and that is exactly what i ended up trying to do. 
I checked all the directories in lost + found and took note of where they belong.

SO for moving them is it just a matter of doing the following for /media ;
> 
root@ubuntu:/mnt/a/lost+found# mv \#586369/ /
bin/        etc/        lib/        proc/       srv/        var/
boot/       home/       media/      rofs/       sys/        vmlinuz
cdrom/      initrd/     mnt/        root/       tmp/        
dev/        initrd.img  opt/        sbin/       usr/        
root@ubuntu:/mnt/a/lost+found# mv \#586369/ /media/


> 1]You have a image of your linux partition stored somewhere so you can restore it.
or
2]You are comfortable with reinstalling because you don't feel it's hard?

I have become very comfortable reinstalling, I have an iso image on a dvd that i can
use, except it is not upgraded and will require about 200mb of downloading.

I did install clonzilla and thought I had made a copy just before my crash but I only see a few directories with not much in them.

---

### Post by meindian523 on 2008-01-10
Um,sorry for being such a jerk,but I didn't get what you meant to say
> 
I checked all the directories in lost + found and took note of where they belong.

SO for moving them is it just a matter of doing the following for /media ;
[QUOTE]
root@ubuntu:/mnt/a/lost+found# mv \#586369/ /
bin/ etc/ lib/ proc/ srv/ var/
boot/ home/ media/ rofs/ sys/ vmlinuz
cdrom/ initrd/ mnt/ root/ tmp/
dev/ initrd.img opt/ sbin/ usr/
root@ubuntu:/mnt/a/lost+found# mv \#586369/ /media/

[/QUOTE]
with this?Did you mean to ask a question "So for moving them is it just a matter of doing the following for /media?"

---

### Post by MoHamm on 2008-01-10
no worries.. 
 
my main question is how do i restore/move the directories in lost and found to their parent   directories in /? I cant see / anywhere.

what i posted was a question. If that is the command to be used to move them over.

another question is, If I move the grub directory first will I be able to start the system and continue the moving process there?

---

### Post by meindian523 on 2008-01-10
1]yup,you use the ```
mv <directory_in_lost+found> /
``` command.You don't need to "see" /.Once you have chrooted,you are using / as your home directory.Just be sure that you have chrooted before you start moving directories around,because if you have not chrooted into your / partition,you would be moving directories of the Live CD which anyway reside in RAM,so it would be a waste of effort.

2]About moving /boot first,I don't think so since even though the kernel and initrd would start up,bash(the command-line shell) wouldn't and neither would your personal settings be used,even assuming that you don't want the graphical interface.

---

### Post by meindian523 on 2008-01-10
Use the graphic I posted earlier,it will help in placing the directories in their proper places.If you want an algorithm,this is what it would look like:

1]Boot into Live CD
2]Open Terminal
3]make a directory in /mnt to mount /dev/sda3(your / partition)
4]mount your / partition
5]chroot into your mounted / partition
6]change directory into lost+found
7]Take a listing of the directories
8]Take a listing of the contents of one of the directories```
ls -l \<number>/
```
9]Refer the graphic.
10]Change the name using the mv command appropriately to reflect the directory's position in /.
11]Go to (8) and repeat till all the directories are renamed appropriately,then just do a ```
mv *.* /
```
12]Reboot and try booting into your Ubuntu installation.

---

### Post by MoHamm on 2008-01-10
EDIT: I just saw your top post disregard this one


so the command to chroot into / is?

> chroot /  

and then to move directory;

> root@ubuntu:/# mv /mnt/a/lost+found/#130305/grub/ /boot

how do I then check if I did the right thing?

much much thanks...

---

### Post by MoHamm on 2008-01-10
Ok it all seems much clearer now, however I am getting this output again when trying to chroot, here it is;

> root@ubuntu:/# chroot /mnt/a/
chroot: cannot run command `/bin/bash': No such file or directory


---

### Post by meindian523 on 2008-01-10
Oh,then we will have to modify the command to move a li'l bit:

```
mv /mnt/a/lost+found/<name_of_directory> /mnt/a
```

---

### Post by meindian523 on 2008-01-10
Please post back the results.

---

### Post by MoHamm on 2008-01-10
excuse the delay, lost connection..

here is the result for one of them

> root@ubuntu:/mnt/a/lost+found# mv \#586369/ media
root@ubuntu:/mnt/a/lost+found# mv /mnt/a/lost+found/media/ /mnt/a/
root@ubuntu:/mnt/a/lost+found# cd ..
root@ubuntu:/mnt/a# ls
lost+found  media
root@ubuntu:/mnt/a# cd media/
root@ubuntu:/mnt/a/media# ls
caps  cdrom  cdrom0  marlinn  sda1  sda2  sda5  sda6  sda8  ubu


seems right.

---

### Post by meindian523 on 2008-01-10
yup,that's correct,just go on and get back your system,I trust that the graphic is helping you?Found it in another thread posted by a mod.... ;) :)

---

### Post by MoHamm on 2008-01-10
ok. I am on it. 
I rebooted and was able to get through the grub, however the system froze and I could not shutdown I had to remove the battery(laptop).

So I am back working the lost and found list of directories and hope to have it fixed soon and post the results

Finally I have a slight idea of what I am doing. 

cheers

.

---

### Post by meindian523 on 2008-01-11
In case of hangs and if you cannot get back control by killing the Xserver by Ctrl+Alt+Backspace,you can use 
Alt+SysRQ(Prt Scr)+R
Alt+SysRQ(Prt Scr)+E
Alt+SysRQ(Prt Scr)+S
Alt+SysRQ(Prt Scr)+U
Alt+SysRQ(Prt Scr)+I
Alt+SysRQ(Prt Scr)+B

to reboot.

---

### Post by MoHamm on 2008-01-11
great. thanks for the tip.

Ok it seems I have a problem with the Gnome Display Manager. 
The boot process finishes the boot splash bar and does some more checks, 
the last visible before the screen flickers a few times and then hangs is;

> Running local boot scripts (rc.local)

when I then press Cntrl-Alt-Del to reboot it gives out

> Stopping Gnome Display Manager

then shuts down.

I am however able to start text mode and work normally. 

There are a few binary files, libraries and X related direectories in the lost & found that I was not sure where to place, this must be the reason.

---

### Post by meindian523 on 2008-01-11
could you give the ls of those files,I would be able to tell you where to put them.

---

### Post by MoHamm on 2008-01-11
hey meindian523
here is a link to the files, there are a lot..
you have been warned

[http://paste.ubuntu-nl.org/51588/](http://paste.ubuntu-nl.org/51588/)

cheers

---

### Post by meindian523 on 2008-01-12
```
#281528 -->/home/<username>/.gnome2 [or] /root/.gnome2
#281463 -->/root/.synaptic
#281527 -->No idea,looks like a strange BASH script.
#281532 -->/home/<username>/.gconfd/ [or] /root/.gconfd
#284086 -->/usr/lib(rename as libgmodule-2.0.la)
#284090 -->/usr/lib(rename as libgthread-2.0.la)
#281531 -->need more clues,maybe ls of directory apps?
#284059 -->No idea,some XML document.
#284084]_-->Both are links,no idea where they can go
#284085]
#284091 -->need cat for meaningful guess
#284092]_-->Both are links,no idea where they can go
#284093]
#284094 -->Didn't find any parallel on my system.
#284096 -->need more details,maybe cat of file?
#297411 -->/home/<username>/.gnupg
#298810 -->/home/<username>/.gstreamer-0.10/registry.i486.xml [or] /root/.gstreamer-0.10/registry.i486.xml
#298855 -->/home/<username>/.nautilus [or] /root/.nautilus
#331406 -->/home/<username>/.thumbnails [or] /root/.thumbnails
#331425 -->/home/<username>/.gnome [or] /root/.gnome
#429004 -->No idea.
#81441 -->No idea.
#439873-->Looks like the settings file for an app called wireshark,should most probably be in /home/<username>/.Wireshark
```

---

### Post by MoHamm on 2008-01-12
Hi there..

I made the adjustments but at reboot the system still hanged in the same place.

 It seems its either a gnome or an Xserver issue since I am not able to go into graphical mode. I am wondering if purging and re-installing gnome is a possible solution, same with X. 

Or just finally settle for a clean re-install of the whole system so as to avoid any future issues due to some gaps i might have made in the system.

This has been a tremendous learning experience worth every minute. I am truely grateful meindian.

---

### Post by meindian523 on 2008-01-12
You might try doing ```
sudo dpkg-reconfigure xserver-xorg
```,that would recreate your settings files back to scratch and if that doesn't work,try ```
sudo apt-get remove gdm 
```and ```
sudo apt-get remove xserver-xorg
``` and again ```
sudo apt-get install gdm
``` and ```
sudo apt-get install xserver-xorg
```

Basically,trying to get back settings files,I think that's the only thing which is stopping X from coming up.
And please refer the comments and try to post the details required for the appropriate files.

---

### Post by MoHamm on 2008-01-13
Unfortunately non of the above worked. :(

I shall settle for a reinstall of the OS, otherwise I risk random issues arising in the future.
Lesson learned is to never run fsck on a mounted partition!!


Thanks meindian. 

EDIT: One last thing, Could /home being on a separate partition with all its contents be causing this?

---

### Post by randcoop on 2008-01-13
I'm probably getting into this too late to help (you've re-installed?), but Grub 15 error is an error indicating that grub cannot find the image file.  Take a look at /boot and look for the img file.  If you don't have it, but have a backup .img (ends in .bak), then copy the .bak file to a file that doesn't end in bak.  My image file is called initrd.img-2.6.22-14-generic for example.  If you have a name like that ending in .bak, copy the .bak to just exactly the same name without bak (ending in generic).  

Then reboot selecting the grub menu selection that corresponds to the kernel number of your image file.

You shouldn't get error 15 if you do this, since that's what error 15 is.

---

### Post by meindian523 on 2008-01-13
@randcoop

The problem is that he ran fsck on a mounted partition(/) and all his folders went to lost+found.So we restored everything and now Ubuntu boots back to command-line but no GUI.

@MoHamm

Those were not supposed to be run one at a time,I gave those commands to:
1]Reconfigure Xorg
If that doesn't work,
2]Remove and Install GDM.
3]Remove and Install X.

---

### Post by meindian523 on 2008-01-14
What happened?

---

