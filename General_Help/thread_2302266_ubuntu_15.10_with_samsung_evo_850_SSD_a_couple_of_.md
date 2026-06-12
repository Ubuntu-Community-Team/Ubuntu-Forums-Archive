---
title: "ubuntu 15.10 with samsung evo 850 SSD a couple of questions"
date: 2015-11-09
forum: General Help
---

### Post by sebastiaan5 on 2015-11-09
Hello,

I will probably buy an SSD for my laptop, the samsung evo 850 250gb.
But I'm wondering what i need to know or to do if I have it, so I have a couple of questions;

laptop specs: lenovo Y50-70 I7 nvidia 860GTX 16GB ram

Is the samsung magician software supported on ubuntu/ubuntu gnome?
Do I need to trim by my self or does it happen automatically?
Do I still need a swap partition?


greetings

---

### Post by sebastiaan5 on 2015-11-09
bump

---

### Post by sebastiaan5 on 2015-11-10
bump

---

### Post by howefield on 2015-11-10
In the absence of any other replies...

> **sebastiaan5 said:**
> Is the samsung magician software supported on ubuntu/ubuntu gnome?

There are downloads for Linux on the [Samsung]("http://www.samsung.com/global/business/semiconductor/minisite/SSD/global/html/support/downloads.html") website - probably your best bet for information on that.

> Do I need to trim by my self or does it happen automatically?

The system will initiate a weekly cron job to trim the drive, so you shouldn't have to worry about that unless you want to vary the frequency or use another method.

> Do I still need a swap partition?

I have swap on a separate mechanical drive, but it is so seldom (almost never) used, the next install will probably see it on the SSD. With 16GB of ram I'd expect you will also almost never use swap. I'm not sure I'd run without one though, if only for misbehaving applications.

One other concession I make is to put the "/home" folders for web browsers, email and a few other applications on a separate mechanical drive to cut down on the writes to the drive, easy on a desktop but perhaps not so on a laptop.

---

### Post by alikazmi-2040 on 2016-06-14
I know this is a very old thread but posting this just in case :), apologies if it causes anyone any inconvenience.

One of the most important things you **should** do if you have Linux (any distro) installed on an SSD is to disable access time logging. Basically, every read causes a write which can reduce the overall life-time of the SSD. In order to disable access time logging, you have to edit and add the 'noatime' flag to each SSD partition in /etc/fstab.

Here's how you will go about doing this:

_**Step 1:**_
$ sudo nano /etc/fstab

_**Step 2:**_
Change

[FONT=courier new]#Entry for /dev/sdb1 :
UUID=b8e8a337-6a74-4335-a6d9-cbb176ad8805    /    ext3    errors=remount-ro    0    1
#Entry for /dev/sdb2 :
UUID=3A532B2B52450842    /media/ikazmi/VMs    ntfs-3g    defaults,locale=en_US.UTF-8    0    0[/FONT]

to

[FONT=courier new]#Entry for /dev/sdb1 :
UUID=b8e8a337-6a74-4335-a6d9-cbb176ad8805    /    ext3    noatime,errors=remount-ro    0    1
#Entry for /dev/sdb2 :
UUID=3A532B2B52450842    /media/ikazmi/VMs    ntfs-3g    defaults,noatime,locale=en_US.UTF-8    0    0[/FONT]

where sdb is the SSD.

Save the file and reboot your system. It will reduce the number of writes quite a bit and increasing the lifetime of your SSD.

---

