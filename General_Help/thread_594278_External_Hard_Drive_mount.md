---
title: "External Hard Drive mount"
date: 2007-10-27
forum: General Help
---

### Post by ChickenDog on 2007-10-27
I am new to Ubuntu.  I have Ubuntu 7.10 installed and i have an exteranl 120 gig NTFS hard drive that i want to access in Ubuntu.  I am assuming i need to install nfts.  When i run sudo apt-get install portmap nfs-common 

I get 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package portmap

I get that last line on everything i run.  

Any help would be great. 

thanks

---

### Post by taurus on 2007-10-27
If you want to use ntfs (read-only) driver, it's already on your system.  Just mount your external drive as

```
sudo mkdir /media/sda1
sudo mount -t ntfs /dev/sda1 /media/sda1
df -h
```
Assuming your external drive is /dev/sda1.

```
sudo fdisk -l
```

---

### Post by ChickenDog on 2007-10-27
thanks Tarus,

This is what i am getting

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 122.9 GB, 122941341696 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0def3d46

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    7  HPFS/NTFS
ben@ben-desktop:~$ sudo mount -t ntfs /dev/sda1 /media/sda1
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
ben@ben-desktop:~$ 

I am assuming it has something to do with the HPFS.  Is this correct?

thanks.
Ben

---

### Post by taurus on 2007-10-27
> **ChickenDog said:**
> thanks Tarus,

This is what i am getting

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 122.9 GB, 122941341696 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0def3d46

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdb1               1       14593   117218241    7  HPFS/NTFS**
ben@ben-desktop:~$ sudo mount -t ntfs /dev/sda1 /media/sda1
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
ben@ben-desktop:~$ 

I am assuming it has something to do with the HPFS.  Is this correct?

thanks.
Ben

Actually, it's /dev/sdb1 since /dev/sda1 is your Ubuntu partition.

```
sudo mkdir /media/sdb1
sudo mount -t ntfs /dev/sdb1 /media/sdb1 -o nls=utf8,umask=0222
ls -la /media
```

---

### Post by ChickenDog on 2007-10-27
Thank you!

---

