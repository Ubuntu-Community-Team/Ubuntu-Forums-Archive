---
title: "Partion with windows issue"
date: 2013-01-12
forum: General Help
---

### Post by Kocrachon on 2013-01-12
Right now I am trying to setup 12.10, and I have windows 7 currently installed.

I removed my 12.04 OS and partion entirely through Windows hardware manager by deleting that partition and re-adding it to my main. I am now trying to reinstall 12.10 after a while, and when I select install beside Windows in the options, it shows my second hard drive, which I use only for game installs. So it shows sdb, not sda. But when I go to manage my own partitions, I see sda. So I want to put it on SDA, but if I do a "new partition table" I will lose everything... So why is it not reconizing the SDA drive on the other option?

---

### Post by fergie716 on 2013-01-12
> **Kocrachon said:**
> Right now I am trying to setup 12.10, and I have windows 7 currently installed.

I removed my 12.04 OS and partion entirely through Windows hardware manager by deleting that partition and re-adding it to my main. I am now trying to reinstall 12.10 after a while, and when I select install beside Windows in the options, it shows my second hard drive, which I use only for game installs. So it shows sdb, not sda. But when I go to manage my own partitions, I see sda. So I want to put it on SDA, but if I do a "new partition table" I will lose everything... So why is it not reconizing the SDA drive on the other option?
I'm no expert, but I would get back into Windows and create a new partition to which you install 12.10 on. If I understand you correctly you just re added the old partition back to Windows but never made another one?

Then when you go through the options for install select "Something Else", select that new partition, select Primary as the type for the new partition, select Beginning of this space for Location,  use as Ext4 and mount point as "/"

Prior to this I made a swap partition (10% of the free space I made in Windows, , Logical partition, use as swap area)

If you can't get back into Windows you can boot from Live CD and use Gparted to make a new partition but I've always been told to use Windows to do this.. Not 100% sure if it matters that much

---

### Post by Kocrachon on 2013-01-13
Essentially that is what I ended up doing. I just went to windows and created the partition. However, its still a bit of a hassle as to why it the option did see the HDD to begin with.

---

### Post by oldfred on 2013-01-14
Do not create partitions in Windows for Linux. Use Windows tools for Windows & Linux tools for Linux.

It may convert to dynamic partitions and then Linux will not ever work as dynamic partitions are proprietary to Windows.

Post this from Ubuntu liveCD/DVD/Flash terminal, if SFS then you have dynamic. Or you will see basic or dynamic in the Windows partitioner.

       sudo fdisk /dev/sda

---

