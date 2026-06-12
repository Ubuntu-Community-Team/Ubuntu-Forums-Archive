---
title: "[SOLVED] Cannot login, HD space full but not"
date: 2008-03-06
forum: General Help
---

### Post by TidusBlade on 2008-03-06
Okay, firstly I'm using Linux Mint 4.0 KDE CE, but I doubt it makes a difference since Mint was built off Ubuntu I think.
Anyways, I was having problems logging in, whenever I type the correct settings it used to refresh the monitor and I find myself back in the login window, even in safe mode...
So I tried using the console login to startx but it returned:
```
mkdir: cannot create directory '/home/tidusblade/.linuxmint': No space left on device
```
I have /dev/sda5 as my / partition, and it's part of extended partition, and itself is a logical partition but I don't think thats a problem because I used it properly before making /dev/sda2 my /home partition. It works as being my home partition but as I said, it said the hard disk is full but theres quite some space left on it, I think about 5GB when I checked using Gparted from a Ubuntu Live CD. My / partiton also got like 9GB left.

Sorry if it was long, but I hope someone will be able to help me :)

Thanks!

---

### Post by dcstar on 2008-03-07
> **TidusBlade said:**
> Okay, firstly I'm using Linux Mint 4.0 KDE CE, but I doubt it makes a difference since Mint was built off Ubuntu I think.
Anyways, I was having problems logging in, whenever I type the correct settings it used to refresh the monitor and I find myself back in the login window, even in safe mode...
So I tried using the console login to startx but it returned:
```
mkdir: cannot create directory '/home/tidusblade/.linuxmint': No space left on device
```
I have /dev/sda5 as my / partition, and it's part of extended partition, and itself is a logical partition but I don't think thats a problem because I used it properly before making /dev/sda2 my /home partition. It works as being my home partition but as I said, it said the hard disk is full but theres quite some space left on it, I think about 5GB when I checked using Gparted from a Ubuntu Live CD. My / partiton also got like 9GB left.

Sorry if it was long, but I hope someone will be able to help me :)

Thanks!

Quotas maybe?, if you posted the actual data from fdisk -l & df -h we might be able to make a better guess.

---

### Post by TidusBlade on 2008-03-07
Thanks alot, but I fixed it, I actually screwed up with making the /home partition so I just fixed it now.

---

