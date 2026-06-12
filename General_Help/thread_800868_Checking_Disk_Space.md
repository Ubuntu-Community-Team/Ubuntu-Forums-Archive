---
title: "Checking Disk Space"
date: 2008-05-20
forum: General Help
---

### Post by Amnesia180 on 2008-05-20
Hi All,

My acer laptop has windows and unbuntu install on it. The installation finished about 10 minutes ago.

I have two partitions Acer (C:) and ACERDATA (D:)

It created another partition on the C: drive, and has now left me with only 300MB on my C:... but it does not display the other partition for Ubuntu.

It has, however, transferred my My Documents folders from Windows. Has this duplicated EVERYTHING, or just pointed it to the right direction on the HDD?

Is there anyway to find out how much space (using linux) these drives have?

Thanks,
Amnesia

---

### Post by brownicb on 2008-05-20
You should be able to look at a graphical representation of your disk using gparted.  
[B]sudo apt-get install gparted

sudo gparted[/B]

You can also use **fdisk -l** if you don't want to install gparted.

---

### Post by ozorba on 2008-05-20
ACERDATA Partition is for hibernation if I am not mistaken. You do not normally see it in Windows. But you can see it in Ubuntu.

Can you tell us how you have installed Ubuntu. Have you used Wubi or have you created a new partition for Ubuntu? We need more information to be able to help.

---

### Post by cdtech on 2008-05-20
> Is there anyway to find out how much space (using linux) these drives have?

df -H

---

### Post by Amnesia180 on 2008-05-20
Hi,

ACERDATA is where I keep my movies, music and pictures. 

I chose the first option when installing Ubuntu and it was supposed to set up a partition on the C: for Windows on one, and Ubuntu on the other.

---

### Post by Amnesia180 on 2008-05-20
> **brownicb said:**
> You should be able to look at a graphical representation of your disk using gparted.  
[B]sudo apt-get install gparted

sudo gparted[/B]

You can also use **fdisk -l** if you don't want to install gparted.


Hi, I try **sudo apt-get install gparted** but it says:

Package gparted is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source.
E: Package gparted has no installation candidate

---

### Post by brownicb on 2008-05-20
Info on how to install Gparted:
[http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_048.html](http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_048.html)

Or you can use the Gparted Live CD:
[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

