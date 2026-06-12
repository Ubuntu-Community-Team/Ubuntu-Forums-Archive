---
title: "Kernel panic on 12.10 64 bit when mounting ntfs partition"
date: 2013-02-14
forum: General Help
---

### Post by Krasen on 2013-02-14
I have a brand new HP Probook 4540S with dual boot Ubuntu 12.10 64 bi and Windows 7 Ultimate 64 bit. Because I need some documents on both OS I''ve created a ntfs partition wich is accesible from both systems. But when i try to mount this partition in Ubuntu I get kernel panic. [http://s7.postimage.org/mc0273l17/2013_02_15_455.jpg](http://s7.postimage.org/mc0273l17/2013_02_15_455.jpg) this is the screen that I get. I might have it as well when eve opening my file browser. Any ideas what can cause this kernel panic, and what soution can be made?

---

### Post by Bufeu on 2013-02-15
> **Krasen said:**
> I have a brand new HP Probook 4540S with dual boot Ubuntu 12.10 64 bi and Windows 7 Ultimate 64 bit. Because I need some documents on both OS I''ve created a ntfs partition wich is accesible from both systems. But when i try to mount this partition in Ubuntu I get kernel panic. [http://s7.postimage.org/mc0273l17/2013_02_15_455.jpg](http://s7.postimage.org/mc0273l17/2013_02_15_455.jpg) this is the screen that I get. I might have it as well when eve opening my file browser. Any ideas what can cause this kernel panic, and what soution can be made?
Hi and welcome to the forum!
Strange...
Can you please post the output of ```
cat /etc/fstab
cat /etc/partitions
sudo df -h
```

---

### Post by Krasen on 2013-02-15
```
 
# /etc/fstab: static file system information.
 
 
#
 
 
# Use 'blkid' to print the universally unique identifier for a
 
 
# device; this may be used with UUID= as a more robust way to name devices
 
 
# that works even if disks are added and removed. See fstab(5).
 
 
#
 
 
# <file system> <mount point> <type> <options> <dump> <pass>
 
 
# / was on /dev/sda5 during installation
 
 
UUID=5e5d18a5-a860-4294-84b9-3629bf51c823 / ext4 errors=remount-ro 0 1
 
 
# swap was on /dev/sda6 during installation
 
 
UUID=6c5127fe-719b-4114-ab9d-504b318e2f19 none swap sw 
 
 
 
 
alcapone@alcapone:~$ cat /etc/partitions
 
 
cat: /etc/partitions: No such file or directory
 
 
 
 
Filesystem Size Used Avail Use% Mounted on
 
 
/dev/sda5 112G 3.8G 103G 4% /
 
 
udev 3.9G 4.0K 3.9G 1% /dev
 
 
tmpfs 1.6G 884K 1.6G 1% /run
 
 
none 5.0M 0 5.0M 0% /run/lock
 
 
none 3.9G 152K 3.9G 1% /run/shm
 
 
none 100M 24K 100M 1% /run/user
 
 
/dev/sdb1 466G 1.6G 465G 1% /media/alcapone/HANDY500

``` 
 
This are the results

---

### Post by Bufeu on 2013-02-15
Sorry, my typo.
Please post the output of *cat /proc/partitons*. Please you the [CODE]-tag.

---

### Post by Krasen on 2013-02-15
I'll post it but when booted the Ubuntu and posted the results the machine freezed. And did not responded the mouse movement and the keboard. Will post the *cat /proc/partitons *in few minutes.

---

### Post by Bufeu on 2013-02-15
Also, what command did you run to mount the NTFS-partition?

---

### Post by Krasen on 2013-02-15
```
   8        0  732574584 sda
   8        1     358400 sda1
   8        2  123504640 sda2
   8        3          1 sda3
   8        4  485664768 sda4
   8        5  119042048 sda5
   8        6    3998720 sda6
  11        0    1048575 sr0
   8       16  488386584 sdb
   8       17  488384001 sdb1

```

This is the cat /proc/partitons

---

### Post by Krasen on 2013-02-15
Manually with
```
 
# sudo mount

```
 
Or just clicking ot the icon on the file browser. But now I have another issue. When posted the output of the fstab, and partitons the machine chrashed both times. After posting the threds it has frozen, and could not do anyting but to use the power button.

---

### Post by Bufeu on 2013-02-15
> **Krasen said:**
> Manually with
```
 
# sudo mount

```Or just clicking ot the icon on the file browser. But now I have another issue. When posted the output of the fstab, and partitons the machine chrashed both times. After posting the threds it has frozen, and could not do anyting but to use the power button.
Please post the ouput of *uname -rpio*.

---

### Post by Krasen on 2013-02-15
```
 
3.5.0-23-generic x86_x64 x86_x64 GNU/Linux

```

---

### Post by Bufeu on 2013-02-15
Did you only ran ```
sudo mount
```and nothing else when trying to mount the drive?

---

### Post by Krasen on 2013-02-15
the path to the drive /sda-what-number-is-the-current-drive then the mount point

---

### Post by Krasen on 2013-02-16
In the past few hour everything that I on my ubuntu leads to kernel panic. With the screen that I have posted in the first thred.

---

### Post by Bufeu on 2013-02-16
Can be a hardware problem. Checked the memory? Have you done a check of the disk(s)?

---

### Post by Krasen on 2013-02-16
On the live Ubuntu there is no problem and the disk and memory chek are ok. On the Windows 7 Ultimate as well the checks are ok. The only difference is the wi-fi driver. The live Ubuntu does not have druver for the card. The card is Ralink rt3290 with driver from the manifacturer. 
 
P.S. I am sorry for my spelling today but I hanvn't slept last night trying to find the problem.

---

### Post by Bufeu on 2013-02-16
Well, I'm running out of ideas... Uninstall the graphics drivers, and see if it solves your problem.
Otherwise, install the linux-headers-package for your kernel. You can install them from a live-CD using *chroot* to change root folder (*/*).

---

### Post by Krasen on 2013-02-16
This is something that might work because I have no idea, haw is Ubuntu dealing with this new two grafic card machines. I'll try this as well.

---

