---
title: "Recover Deleted, but not formatted NTFS partition"
date: 2008-04-20
forum: General Help
---

### Post by earthmeLon on 2008-04-20
Hey guys, I've had this problem for a couple of days now, and after hours of research, asking a couple of my friends, and getting on the irc server, I am still unable to find a solution.  I hope posting my problem here will help get an answer.


When I installed Ubuntu on my AMD64 computer, the partition manager was unable to read the HDD that I wanted to install Ubuntu on.  This HDD has 4 partitions.  Linux swap, Root, /home and an NTFS partition with all my pictures, programming projects, chat logs, game installs, etc.

I was able to get the partition manager to read the HDD by deleting and re-creating the NTFS partition (/dev/sda2) because when I created the partition using Windows, it created it one cylinder over the HDD's capacity.  I then successfully installed Ubuntu ^_^.

Oh noes!  I am unable to mount the NTFS partition.  I added sda2 to my fstab list, and when I try sudo mount -a I get this error:
```
NTFS signature is missing.
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```


I used FDISK to delete/re-create the partition.  I have not formatted it or anything.  I've followed some direction from [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) with no success.

I've been trying to recover the partition with it as free space, and as it as NTFS (using FDISK to switch between the two) because I'm not sure if the recovery programs want to see it as either, but haven't gotten it to work.

Any suggestions would be greatly appreciated!
Thanks in advance!

---

### Post by -Zeus- on 2008-04-21
I'm not sure if you could recover that without taking it to some data service.

---

### Post by ryanhaigh on 2008-04-21
I believe testdisk is the best application available under ubuntu for recovering information about partition tables.

The only other application I have ever used is ARDC data recovery tools, google should help you find it. You will need a windows install to use it (if you don't have one take your hd to a friends do not put anything else on the disk you are trying to recover). ARDC is also free.

---

### Post by RobHK on 2008-04-21
I've had a lot of success with Acronis Recovery Expert, part of Acronis Disk Director Suite. It's a Windows program, but if you have access to a Windows installation you can make a boot disk. It's not free in either sense, but you can run the demo to see if your partition is recoverable, and only buy it if it is.

Obviously don't do anything on the disk where your lost partition is.

---

### Post by earthmeLon on 2008-04-21
Thanks for the replies.  I just returned home from work and got myself a nice 500g HDD on my way :D

I'm going to try to recover the data on the partition, instead of the actual partition.  My friend is coming over and plans to use dd, or ddrescue.  I'll let you guys know how that works out.  If it doesnt, he's bringing his laptop (with windows), So I'll try those other ideas.

---

### Post by Old Marcus on 2008-04-21
I had a lot of success recovering files from a USB stick i wiped using photorec, under the testdisk program. But if Ubuntu's gone that's probably not possible. :p

---

### Post by earthmeLon on 2008-04-21
Ubuntu is here; I only lost a personally important partition, not a partition important to the system.  I am currently in the process of creating an img using dd. 200GB/250GB in the img so far.

I can't wait for it to finish :D

---

### Post by earthmeLon on 2008-04-24
Well, I was unable to recover the partition, although I was able to extract certain types of files off of the partition.  The types of files it will allow me to extract, and the manner in which it saves them (random filenames in one directory) makes it pretty much useless.

I've got the image an external HDD and I'll probably keep it there praying I learn of a better way to extract some information.


Thanks for the help guys :D

---

