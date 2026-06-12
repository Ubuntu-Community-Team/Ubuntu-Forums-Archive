---
title: "How do I mount my Home folder from live usb"
date: 2023-05-08
forum: General Help
---

### Post by Evil Wayz on 2023-05-08
My system is hopelessly hosed.   I need to know how to mount my Home folder so I can copy my files and start over.

---

### Post by yancek on 2023-05-08
You would first need to boot your 'live' Ubuntu (or other Linux usb/dvd) and open a terminal and execute this command:

```
 sudo fdisk -l
```

THis will list the partitions on the disk.  Do you have /home on a separate partition?  If not, whichever partition shows as a Linux filesystem would be it so you should be able to do:

```
sudo mount /dev/sda1 /mnt
```  

The above assumes the Linux filesystem is sda1 so you will need to change that if that is not the correct partition.

---

### Post by Evil Wayz on 2023-05-08
> **yancek said:**
> You would first need to boot your 'live' Ubuntu (or other Linux usb/dvd) and open a terminal and execute this command:

```
 sudo fdisk -l
```

THis will list the partitions on the disk.  Do you have /home on a separate partition?  If not, whichever partition shows as a Linux filesystem would be it so you should be able to do:

```
sudo mount /dev/sda1 /mnt
```  

The above assumes the Linux filesystem is sda1 so you will need to change that if that is not the correct partition.

Thank you.  still says permission denied,  is there a chown command I need to run?  I know the password for this user as it's me.

---

### Post by Impavidus on 2023-05-08
Your userID on the live system is different from your userID on the installed system, therefore you get permission denied. Your userID on the installed system doesn't even exist on the live system. Easiest is to use sudo to copy the files to your backup drive.

---

### Post by yancek on 2023-05-08
I would suggest you run the commands again and post the command along with the output as it is possible to leave a needed character out of the command.
If you post the fdisk output and have more than one Linux partition, indicate which you think is the /home partition if it is separate.  You would not 'mount' your user home folder, you need to mount the filesystem on the partition on which it resides.  If you haven't resolved this, post the commands and output here.  Do you get the permission denied when you try to mount only?  If you are using Ubuntu, post the release version also.

---

### Post by ne29914 on 2023-05-08
I don't see the reason for mounting the desired file system under /mnt.
If it's a "monolithic" file system with just one partition, just mount it as /.
```
sudo mount /dev/sda1 /
```
If there's a separate /home partition, mount that as /home.
```
sudo mount /dev/sda2 /home
```
Haven't had problems with that.

---

### Post by C.S.Cameron on 2023-05-09
Persistence Files and Partitions

Writable, (casper-rw) and home-rw persistence overlays may exist as files located on any FAT32 drive partition or as individual ext 2,3, or 4 partitions on the drive. Persistent files are limited to 4GB, nowadays so most Persistent Live Ubuntu USB's use persistent partitions.

Persistent USB creators such as Rufus and mkusb create a file structure inside the Persistent partition in a directory named "upper". You can mount this partition using Disks.

"Upper" contains the overlay files and folders used for persistence. You can find your home folder there.

You can also just copy the casper-rw or writable partition to a new Live USB using GParted copy / paste. You may need to add the word "persistent" to the linux line in GRUB.

---

### Post by Impavidus on 2023-05-09
> **ne29914 said:**
> I don't see the reason for mounting the desired file system under /mnt.
The purpose is it access the filesystem on the internal drive from the live disk. Then you can't mount it on a directory where it would hide important parts of the live system's filesystem, as that would break the live session.

---

### Post by ne29914 on 2023-05-09
Ah, that makes sense. I always have /home on a separate partition, so it's no problem mounting it directly as /home.
I can see the problem with /

---

