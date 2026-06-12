---
title: "Booting Ubuntu From a extended Partition"
date: 2008-06-12
forum: General Help
---

### Post by Bunni on 2008-06-12
Im having trouble trying to boot a ubuntu installation off a extended partition, currently on the drive in question (sdb) i have:
extended:
/dev/sdb1
   /dev/sdb5 ntfs
   /dev/sdb6 ext3 (seperate ubuntu (one i want to get working))

/dev/sdb2 ext3 (ubuntu)
/dev/sdb3 swap
/dev/sdb4 ext3

heres my device map
```

(hd0)	/dev/hda
(hd1)	/dev/hdb
(hd2)	/dev/sda
(hd3)	/dev/sdb
```
and my current menu.lst
```

title		Ubuntu 8.04
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=82cf780c-8499-46ff-8de9-06273aa3294f ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04 (recovery mode)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=82cf780c-8499-46ff-8de9-06273aa3294f ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04 (this is the one i want ot get working)
root 		(hd3,5)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=82cf780c-8499-46ff-8de9-06273aa3294f ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04 (one i want to get working)
root		(hd3,5)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=82cf780c-8499-46ff-8de9-06273aa3294f ro single
initrd		/boot/initrd.img-2.6.24-18-generi

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

any and all help will be greatly appreciated!

---

### Post by meierfra. on 2008-06-12
Try

title		Ubuntu 8.04 on sdb6
root 		(hd3,5)
kernel		/vmlinuz root=/dev/sdb6 ro quiet splash
initrd		/initrd.img
quiet

title		Ubuntu 8.04 recovery on sdb6
root		(hd3,5)
kernel		/vmlinuz root=/dev/sdb6  ro single
initrd		/initrd.img


Also you should put these items below the line
### END DEBIAN AUTOMAGIC KERNELS LIST
Otherwise they will disappear after the next sdb2 kernel update.

---

### Post by Bunni on 2008-06-16
grub gives me a error 2 message: "bad file or directory type"

---

### Post by meierfra. on 2008-06-16
Lets see whether whether you can mount your  sdb6 partition.

Boot into the ubuntu on sdb2. Open a terminal and post the output of 

```
mkdir sdb6
sudo mount -t ext3 /dev/sdb6  sdb6
ls -l sdb6/boot
ls -l sdb6/boot/grub
```


To you use any kind of raid?

Just for double checking, post your men.lst item for the Ubuntu on sdb6.

Also post the full output of 

```
sudo fdisk -l
```

---

### Post by Bunni on 2008-06-17
```
mkdir sdb6
sudo mount -t ext3 /dev/sdb6  sdb6
ls -l sdb6/boot
ls -l sdb6/boot/grub
```
> bunni@Synergy:~$ mkdir sdb6
mkdir: cannot create directory `sdb6': File exists
bunni@Synergy:~$ sudo mount -t ext3 /dev/sdb6  sdb6
mount: special device /dev/sdb6 does not exist
bunni@Synergy:~$ ls -l sdb6/boot
ls: cannot access sdb6/boot: No such file or directory
bunni@Synergy:~$ ls -l sdb6/boot/grub



```
sudo fdisk -l
```
After disabling my raid array this is the output:
> Disk /dev/sda: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4651a0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4865    39078081    7  HPFS/NTFS
/dev/sda2            4866        9732    39094177+   f  W95 Ext'd (LBA)
/dev/sda5            4866        9732    39094146    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00043c70

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sdb2            1276        2550    10241437+   7  HPFS/NTFS
/dev/sdb3            2551        4865    18595237+   7  HPFS/NTFS

Disk /dev/sdc: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10d210d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9038    72597703+   7  HPFS/NTFS

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f800000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               2       17663   141870015    f  W95 Ext'd (LBA)
/dev/sdd2           17664       19274    12940357+  83  Linux
/dev/sdd3           19275       19456     1461915   82  Linux swap / Solaris
/dev/sdd4           19457       19457        8032+  83  Linux
/dev/sdd5               2       15299   122881153+   7  HPFS/NTFS
/dev/sdd6   *       15300       17663    18988798+  83  Linux


---

### Post by meierfra. on 2008-06-17
What is you current situation (after disabling the raid)?  Are still able to boot  into the Ubuntu on the primary partition?  Do you still get error 2 when trying to boot the other ubuntu?

> 
mount: special device /dev/sdb6 does not exist

Disabling the raid, changed the device names. So try


> mkdir sdd6
sudo mount -t ext3 /dev/sdd6  sdd6
ls -l sdd6/boot
ls -l sdd6/boot/grub

---

### Post by louieb on 2008-06-17
May not work with raid but its easy and worth a shot. Have your 1st Ubuntu GRUB load the 2nd installs menu.lst via the configfile option.

```
title  configfile to load a menu.lst
configfile (hd1,5)/boot/grub/menu.lst  

```

Once you get the (hd#,#) part right  2nd Ubuntu installs menu.lst should be used.

---

### Post by Bunni on 2008-06-17
> **meierfra. said:**
> What is you current situation (after disabling the raid)?  Are still able to boot  into the Ubuntu on the primary partition?  Do you still get error 2 when trying to boot the other ubuntu?



Disabling the raid, changed the device names. So try

Looks like it worked
> bunni@Synergy:~$ mkdir sdd6
mkdir: cannot create directory `sdd6': File exists
bunni@Synergy:~$ sudo mount -t ext3 /dev/sdd6 sdd6
mount: /dev/sdd6 already mounted or sdd6 busy
mount: according to mtab, /dev/sdd6 is mounted on /home/bunni/sdd6
bunni@Synergy:~$ ls -l sdd6/boot
abi-2.6.22-14-generic             initrd.img-2.6.24-17-generic.bak
abi-2.6.24-17-generic             initrd.img-2.6.24-18-generic
abi-2.6.24-18-generic             initrd.img-2.6.24-18-generic.bak
config-2.6.22-14-generic          memtest86+.bin
config-2.6.24-17-generic          System.map-2.6.22-14-generic
config-2.6.24-18-generic          System.map-2.6.24-17-generic
grub                              System.map-2.6.24-18-generic
initrd.img-2.6.22-14-generic      vmlinuz-2.6.22-14-generic
initrd.img-2.6.22-14-generic.bak  vmlinuz-2.6.24-17-generic
initrd.img-2.6.24-17-generic      vmlinuz-2.6.24-18-generic

total 468
-rw-r--r-- 1 root root    120 2008-06-12 12:41 device.map
-rw-r--r-- 1 root root   8052 2008-03-16 08:27 e2fs_stage1_5
-rw-r--r-- 1 root root   7888 2008-03-16 08:27 fat_stage1_5
-rw-r--r-- 1 root root   7140 2008-03-16 08:27 ffs_stage1_5
-rw------- 1 root root   1303 2008-06-12 12:41 grub.conf
-rw-r--r-- 1 root root    178 2008-04-19 03:06 grub.conf.old.add
-rw-r--r-- 1 root root    484 2008-04-19 03:02 grub.conf.old.remove
-rw-r--r-- 1 root root   1624 2008-03-16 08:27 grub.conf.sample
-rw-r--r-- 1 root root   7128 2008-03-16 08:27 iso9660_stage1_5
-rw-r--r-- 1 root root   8604 2008-03-16 08:27 jfs_stage1_5
lrwxrwxrwx 1 root root      9 2008-06-12 12:14 menu.lst -> grub.conf
-rw-r--r-- 1 root root   7324 2008-03-16 08:27 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-03-16 08:27 reiserfs_stage1_5
-rw-r--r-- 1 root root  26262 2008-03-16 08:27 splash.xpm.gz
-rw-r--r-- 1 root root    512 2008-03-16 08:27 stage1
-rw-r--r-- 1 root root 104500 2008-03-16 08:27 stage2
-rw-r--r-- 1 root root 104500 2008-03-16 08:27 stage2_eltorito
-rw-r--r-- 1 root root 104484 2008-03-12 17:40 stage2.old
-rw-r--r-- 1 root root   7480 2008-03-16 08:27 ufs2_stage1_5
-rw-r--r-- 1 root root   6704 2008-03-16 08:27 vstafs_stage1_5
-rw-r--r-- 1 root root   9300 2008-03-16 08:27 xfs_stage1_5
bunni@Synergy:~$ 



Though its strange bc look at my device map
> (hd0)	/dev/hda
(hd1)	/dev/hdb
(hd2)	/dev/sdabunni@Synergy:~$ ls -l sdd6/boot/grub 
(hd3)	/dev/sdb

and yet look at my mnu.lst from my first post its still going on the sdb and the first ubuntu loads up fine...
so should i add a new line to device map for the drive? 
(hd4) /dev/sdd

then the menu.lst item would be hd4,5 right?

---

### Post by meierfra. on 2008-06-17
Don't  worry about the device.map. It's hardly ever used.

What was the output of "ls -l sdd6/boot/grub" ?  
Was is blank? (edit: never mind, I found it)

If you have "menu.lst" in "sdb6/boot/grub" you might try  louieb's method, use:

```
configfile (hd3,5)/boot/grub/menu.lst
```


> rw-r--r-- 1 root root 7779482 2008-05-09 07:41 initramfs-genkernel-x86-2.6.25-sabayon

You never told us that you are using sabayon.


What error message do you get then you try to boot  the second ubuntu?

try

title Ubuntu 8.04 on sdd6
root (hd3,5)
kernel /boot/kernel-genkernel-x86-2.6.25-sabayon root=/dev/sdd6 ro 
initrd /boot/initramfs-genkernel-x86-2.6.25-sabayon

---

### Post by Bunni on 2008-06-17
i tried the config line and it seems that grub cannot see that partition at all. In grubs line editor i tried partitions 2-6 and get bad file type...

Im confused why does fdisk show the drive as sdd while grub recognizes it as sdb? Ubuntus startup line is hd3,1 does this mean that the partitions are recognized as #-1 in grub? 

As of right now it seems like in grub hd3,5 is pointing to some ntfs system which would result in that kind of a error right? Could it be that the partition is in a extended partition?

---

### Post by meierfra. on 2008-06-17
> while grub recognizes it as sdb? 

grub does not see it as sdb. The device map has been created then Ubuntu was installed. It has  not  been updated  since then, since it is not being  used. So the content of device.map is irrelevant.


> i tried the config line a

Could you post the content  "grub.conf" in the sabayon grub folder? 

> 
Ubuntus startup line is hd3,1

Grubs starts counting at zero. So (hd3,1) is the 2nd partition on 4th hard drive. (which is the same as /dev/sdd2.
(hd3,5) is the 6th partition on the 4th hard drive (so /dev/sdd6)


> get bad file type...
Error 2 is often caused by raid. So you might check you bios setting whether  your raid is completely disabled. Or check for any other kind of setting which might make a difference.

It also could mean that there is something wrong with the file system on sdd6.
So lets run a file system check:

```

sudo umount /dev/sdd6
sudo e2fsck -C0 -fpv /dev/sdd6
``````

```

---

### Post by meierfra. on 2008-06-17
Maybe  there is a problem with using symlinks. These two options don't involve any symlinks:

title Ubuntu 8.04 on sdd6
root (hd3,5)
kernel /boot/kernel-genkernel-x86-2.6.25-sabayon root=/dev/sdd6 ro
initrd /boot/initramfs-genkernel-x86-2.6.25-sabayon


and

title Ubuntu 8.04  via grub.conf
configfile (hd3,5)/boot/grub/grub.conf

---

### Post by louieb on 2008-06-17
Just out curiosity let GRUB do the searching for you.   At the **grub> ** prompt  see what **find /boot/grub/menu.lst **and find** /grub/menu.lst** returns.

The 2nd find is useful if you have a separate /boot partition. Then if either  finds something besides the 1st distros menu.lst use that in the configfile statement. 

And thats all I can think of to try.  (note if your running grub from a terminal window be sure to use **sudo grub **(run as root) or the find command will not find anything).

---

### Post by meierfra. on 2008-06-17
> ust out curiosity let GRUB do the searching for you. At the grub>  prompt see what find /boot/grub/menu.lst and find /grub/menu.lst returns.


Good  idea. You should also do this  at the grub menu at boot up. Press "c" at the grub menu and then

```

find   /boot/grub/menu.lst
find   /boot/grub/grub.conf
find   /grub/menu.lst
find   /grub/grub.conf
```

What is on /dev/sdd4?

---

### Post by Bunni on 2008-06-18
> **meierfra. said:**
> grub does not see it as sdb. The device map has been created then Ubuntu was installed. It has  not  been updated  since then, since it is not being  used. So the content of device.map is irrelevant.




Could you post the content  "grub.conf" in the sabayon grub folder? 

> # grub.conf generated by the Sabayon Linux Installer
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd1,5)
#          kernel /boot/kernel-genkernel real_root=UUID=cadf568e-4c3d-4206-b956-6777cfd86415
#          initrd /boot/initramfs-genkernel
#boot=sda
default=0
timeout=6
splashimage=(hd1,5)/boot/grub/splash.xpm.gz
title Sabayon Linux x86 3.5 (genkernel-x86-2.6.25-sabayon)
	root (hd1,5)
	kernel /boot/kernel-genkernel-x86-2.6.25-sabayon  root=/dev/ram0 ramdisk=8192 real_root=UUID=cadf568e-4c3d-4206-b956-6777cfd86415 dolvm  quiet  init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 resume=swap:/dev/sdb3
	initrd /boot/initramfs-genkernel-x86-2.6.25-sabayon

title Sabayon Linux x86 3.5 (genkernel-x86-2.6.25-sabayon) (safe mode)
	root (hd1,5)
	kernel /boot/kernel-genkernel-x86-2.6.25-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=cadf568e-4c3d-4206-b956-6777cfd86415 dolvm init=/linuxrc CONSOLE=/dev/tty1 resume=swap:/dev/sdb3 nox acpi=off ide=nodma vga=normal
	initrd /boot/initramfs-genkernel-x86-2.6.25-sabayon

title Other Operating System - Microsoft Windows
	rootnoverify (hd1,5)
	chainloader +1
and its device map
```
# this device map was generated by the Sabayon Linux Installer
(fd0)     /dev/fd0
(hd0)     /dev/sda
(hd1)     /dev/sdb
```
```

sudo umount /dev/sdd6
sudo e2fsck -C0 -fpv /dev/sdd6
```

```
bunni@Synergy:~$ sudo umount /dev/sdd6
bunni@Synergy:~$ sudo e2fsck -C0 -fpv /dev/sdd6
                                                                               
  523301 inodes used (11.02%)
     501 non-contiguous inodes (0.1%)
         # of inodes with ind/dind/tind blocks: 22514/178/0
 3271018 blocks used (68.90%)
       0 bad blocks
       1 large file

  447514 regular files
   39114 directories
    1163 character device files
    4099 block device files
       1 fifo
       0 links
   31400 symbolic links (31052 fast symbolic links)
       1 socket
--------
  523292 files

```

---

### Post by Bunni on 2008-06-18
> **meierfra. said:**
> Good  idea. You should also do this  at the grub menu at boot up. Press "c" at the grub menu and then

```

find   /boot/grub/menu.lst
find   /boot/grub/grub.conf
find   /grub/menu.lst
find   /grub/grub.conf
```

What is on /dev/sdd4?
```
grub> find /boot/grub/menu.lst
find /boot/grub/menu.lst
 (hd3,1)
 (hd3,5)
grub> find /boot/grub/grub.conf
find /boot/grub/grub.conf
 (hd3,5)
grub> find /grub/menu.lst
find /grub/menu.lst

Error 15: File not found
grub> find /grub/grub.conf
find /grub/grub.conf

Error 15: File not found
grub> 

```
is whats returned

---

### Post by Bunni on 2008-06-18
Heres something interesting in command line at the boot menu
find /boot/grub/menu.lst only returns
(hd3,1)
while
find /boot/grub/grub.conf
find /grub/menu.lst
find /grub/grub.conf
return error 15: file not found
:confused:

---

### Post by meierfra. on 2008-06-18
So the file system is  o.k. "root (hd3,5)" is correct but:

 **the bios are unable to find files on sdd6**


Some bios are only able to see the first 130 GB of your hard drive.  (but usually this causes error 18 and not error 2)

You  could  copy  the Sabayon boot folder to the ubuntu partition and see whether that solves the problem


```

sudo  mkdir /Sabayon
sudo  mount /dev/sdd6 sdd6
sudo cp -rpv  sdd6/boot/* /Sabayon
```


Add this to the Ubuntu menu.lst:

title Sabayon Linux x86 3.5 (genkernel-x86-2.6.25-sabayon)
root (hd3,1)
kernel /Sabayon/kernel-genkernel-x86-2.6.25-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=cadf568e-4c3d-4206-b956-6777cfd86415 dolvm quiet init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 resume=swap:/dev/sdd3
initrd /Sabayon/initramfs-genkernel-x86-2.6.25-sabayon

(use copy and paste, make sure  what you don't insert any line brakes in the long "kernel" line)

---

### Post by Bunni on 2008-06-19
> **meierfra. said:**
> So the file system is  o.k. "root (hd3,5)" is correct but:

 **the bios are unable find files on sdd6**


Some bios are only able to see the first 130 GB of your hard drive.  (but usually this causes error 18 and not error 2)

You  could  copy  the Sabayon boot folder to the ubuntu partition and see whether that solves the problem


```

sudo  mkdir /Sabayon
sudo  mount /dev/sdd6 sdd6
sudo cp -rpv  sdd6/boot/* /Sabayon
```


Add this to the Ubuntu menu.lst:

title Sabayon Linux x86 3.5 (genkernel-x86-2.6.25-sabayon)
root (hd3,1)
kernel /Sabayon/kernel-genkernel-x86-2.6.25-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=cadf568e-4c3d-4206-b956-6777cfd86415 dolvm quiet init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 resume=swap:/dev/sdd3
initrd /Sabayon/initramfs-genkernel-x86-2.6.25-sabayon

(use copy and paste, make sure  what you don't insert any line brakes in the long "kernel" line)

That did it! Thank you!!!!!!

---

