---
title: "Windows reinstall fails, takes everything with it."
date: 2007-08-05
forum: General Help
---

### Post by jusmurph on 2007-08-05
I had a disk set up with the first partition as Windows Install, second Linux, third swap, forth blank (8mb), fifth home and sixth (extended) was a general partition.

I need to reinstall windows so i did some research and found how to re install the grub etc. However this is what happened:

I went to reinstall windows, deleted the windows partition and then went to install and it said there was two many partitions, It simply refused to make a partition. So i decided to reboot into Ubuntu and merge the home & general partition as one. I had to restore  which was now on "hd0,0" (previously hd0,0).

I here reboot and got grub back and got Error 17, could not mount disk... so i edited it to point ot hd0,0 and then a longer than usual text start up began, One file failed and i had only booted a terminal screen (no gui Ubuntu).

So then i booted back into the live disk to use that gparted and got the following return in the terminal

```
ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 1.7.1
automounting disabled
======================
Can't have overlapping partitions.


```

Although fdisk shows differently...

```
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            3825        8687    39062047+  83  Linux
/dev/sda2            8688        9295     4883760   82  Linux swap / Solaris
/dev/sda3            9296       48641   316046745    5  Extended
/dev/sda4           24327       48641   195310237+  83  Linux
/dev/sda5            9296       24325   120728412   83  Linux
```

I need to get gparted working, so i can merge the last 2 partitions and then install windows and get my dual boot working. 

Any help will be appreciated greatly, thanks.

---

### Post by logos34 on 2007-08-05
> I here reboot and got grub back and got Error 17, could not mount disk... so i edited it to point ot hd0,0 and then a longer than usual text start up began, One file failed and i had only booted a terminal screen (no gui Ubuntu).


it's having trouble with the other partitions since they've changed and no longer match fstab file.  Try editing /etc/fstab to make it correspond to the new layout.  Take out the UUID's, just use '/dev/sda_' format.  Or just comment out (by placing a '#' hash mark at the beginning of each line) all the partitions except root and swap.  See if that allows you to boot.

---

### Post by jusmurph on 2007-08-05
> **logos34 said:**
> it's having trouble with the other partitions since they've changed and no longer match fstab file.  Try editing /etc/fstab to make it correspond to the new layout.  Take out the UUID's, just use '/dev/sda_' format.  Or just comment out (by placing a '#' hash mark at the beginning of each line) all the partitions except root and swap.  See if that allows you to boot.

How do i do that? I mean can you please elaborate a bit.

I know how to launch that in gedit but it sort of stops there. I assume i have to do that from the installed ubuntu command thing rather than the live cd?

---

### Post by logos34 on 2007-08-05
> I know how to launch that in gedit but it sort of stops there. I assume i have to do that from the installed ubuntu command thing rather than the live cd?

You can edit files on root from the live cd, the partition just needs to be mounted.  In nautilus browser you should be able to mount root by merely clicking on it (if this is the Feisty live cd). It will mount as '/media/disk'.  Then,

**cd /media/disk**
**gksudo gedit /etc/fstab**

Take out the old entries and put in the new ones, something like this:

> /dev/sda4 /media/sda4 ext3 defaults 0 2
/dev/sda5 /media/sda5 ext3 defaults 0 2

you don't need one for the extended partition-it just contains the others

---

### Post by jusmurph on 2007-08-05
> **logos34 said:**
> You can edit files on root from the live cd, the partition just needs to be mounted.  In nautilus browser you should be able to mount root by merely clicking on it (if this is the Feisty live cd). It will mount as '/media/disk'.  Then,

**cd /media/disk**
**gksudo gedit /etc/fstab**

Take out the old entries and put in the new ones, something like this:



you don't need one for the extended partition-it just contains the others

```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda2 swap swap defaults 0 0
```

Thats what i have. Am i to remove it all?

---

### Post by logos34 on 2007-08-05
that's the entry for the live cd.  You need to get into /etc/fstab on the ROOT partition as I explained above.  Won't it mount?

---

### Post by jusmurph on 2007-08-05
> **logos34 said:**
> that's the entry for the live cd.  You need to get into /etc/fstab on the ROOT partition as I explained above.  Won't it mount?

Ok i found it. I could not cd there and get it to work however, this worked

```
sudo gedit /media/disk/etc/fstab
```

This is how it looks now, before i play with it:

```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=9db4f0fe-9fb4-4a0e-9c9f-4a4ae402d2b7 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=aeabc8f7-ea0a-4a79-9716-fffb9367ca7f /Linux ext3 defaults 0 2
# Entry for /dev/sda6 :
UUID=af4079a1-31e9-416b-bae8-612420052390 /home ext3 defaults 0 2
# Entry for /dev/sda1 :
UUID=5E88BAF388BAC933 /media/sda1 ntfs-3g defaults,locale=en_AU.UTF-8 0 1
# Entry for /dev/sdb1 :
UUID=0E58C01758BFFF87 /media/sdb1 ntfs-3g defaults,locale=en_AU.UTF-8 0 1
# Entry for /dev/sdb4 :
UUID=F66CFEBA6CFE7529 /media/sdb4 ntfs-3g defaults,locale=en_AU.UTF-8 0 1
# Entry for /dev/sdc1 :
UUID=6269000968FFDA2D /media/sdc1 ntfs-3g defaults,locale=en_AU.UTF-8 0 1
# Entry for /dev/sdc2 :
UUID=EEE49321E492EADB /media/sdc2 ntfs-3g defaults,locale=en_AU.UTF-8 0 1
# Entry for /dev/sdd1 :
UUID=A8E01779E0174D46 /media/sdd1 ntfs-3g defaults,locale=en_AU.UTF-8 0 1
# Entry for /dev/sda3 :
UUID=2ed760e5-0603-4807-9d5e-5912d1d05bb0 none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hda /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
```

I'm a bit confused, from what I read there is one missing completely?

---

### Post by logos34 on 2007-08-05
this is your fstab reflecting the state of things before you deleted windows (sda1).  Now ubuntu root is sda1, and everything moved up one.  So you need to take out windows line and edit the others to conform to what fdisk is showing.  try this:

> 
[B]/dev/sda1 / ext3 defaults,errors=remount-ro 0 1
/dev/sda4 /Linux ext3 defaults 0 2
/dev/sda5  /home ext3 defaults 0 2[/B]
# Entry for /dev/sdb1 :
UUID=0E58C01758BFFF87 /media/sdb1 ntfs-3g defaults,locale=en_AU.UTF-8 0 1
# Entry for /dev/sdb4 :
UUID=F66CFEBA6CFE7529 /media/sdb4 ntfs-3g defaults,locale=en_AU.UTF-8 0 1
# Entry for /dev/sdc1 :
UUID=6269000968FFDA2D /media/sdc1 ntfs-3g defaults,locale=en_AU.UTF-8 0 1
# Entry for /dev/sdc2 :
UUID=EEE49321E492EADB /media/sdc2 ntfs-3g defaults,locale=en_AU.UTF-8 0 1
# Entry for /dev/sdd1 :
UUID=A8E01779E0174D46 /media/sdd1 ntfs-3g defaults,locale=en_AU.UTF-8 0 1
**/dev/sda2 none swap sw 0 0**

---

### Post by jusmurph on 2007-08-05
Ok thats got Ubuntu booting fine now thank you.

However Gparted is still showing an unallocated disk. With the terminal out put:
```
======================
libparted : 1.7.1
automounting disabled
======================
Can't have overlapping partitions.


```

---

### Post by jusmurph on 2007-08-07
I refered to [this]("http://ubuntuforums.org/showthread.php?t=125048") thread and when i look at my fdisk -l output above, there is no over lapping that i can see?

Is the fact that i changed reference points effecting gparted's ability to read the partition table.

---

### Post by jusmurph on 2007-08-07
When i get home i will give [Test Disk a whirl.]("http://www.cgsecurity.org/wiki/TestDisk_Download") Trying what[ this guy]("http://gparted-forum.surf4.info/viewtopic.php?pid=4255") discovered.

---

