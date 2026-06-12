---
title: "Want to triple boot - XP Vista Ubuntu 710"
date: 2007-11-18
forum: General Help
---

### Post by errolgreer on 2007-11-18
I

---

### Post by malfist on 2007-11-18
I think both XP and Vista require themselves to be the first partition of the first harddrive, I don't think it is possible for both to be installed.

---

### Post by teryowen on 2007-11-18
heres what i think you should do, 

Install XP on one partition, then Vista on another no need to worry about dual boot yet.

Then Install Ubuntu on the 3rd partition, now Ubuntu should detect the other 2 Windows partions and add them to the grub file. But if it doesnt you will just have to edit it you self so that you can boot from the grub to any of the three.

EDIT: are you doing this on multiple Hard drives or only on 1.

---

### Post by WiFi Ed on 2007-11-18
Here's how I did it with 2 hard drives:

First I installed XP onto first hd, then partitioned it (with Acronis partitioning app), one partition for XP, one for Ubuntu. Then I installed Vista onto the entire second hd. Vista detected XP and setup a dual-boot screen where I can choose which OS to load. Then I installed Ubuntu onto the second partition of the first hd, using Ubuntu's partitioning tool during the installation process to setup root, home and swap partitions within the second partition of the first hd.

Ubuntu detected the Windows installation and added it to it's boot manager (grub). When the pc starts, the Ubuntu boot manager pops up and I can choose Ubuntu or Windows. If I choose Windows, the Windows boot manager loads and I can choose XP or Vista.

After I was sure everything was working I "activated" the Windows installations to keep MS happy...

---

### Post by errolgreer on 2007-11-19
Hi all.
I have 2 hard drives. On the first, I have a C drive, which only has the boot.ini on it. This points to the D partition which has XP Pro installed. I then created a new partition and installed Vista (Business) on that one. When I boot the computer I can chooses to boot into XP or vista.

I then added a new hard drive, used the Ubuntu partition editor to create 2 partitions on it, the first of 16 GB formatted to EXT3 and the second a 2GB swap file.

Now, do I boot from the Ubuntu CD and run Install ? If so, what steps do I take to make sure that it goes onto the prepared partition on the 2nd hard drive, and most important, will it update the logon menu to choose which system to boot to, without srewing up the boot loader ? 

Cheers, Errol

---

