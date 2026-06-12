---
title: "how to resize a partition?"
date: 2016-11-30
forum: General Help
---

### Post by yodayams on 2016-11-30
I have Ubuntu 16.04 LTS, I want to resize my partition. How can I do this?

---

### Post by Quarkrad on 2016-11-30
Would help to have a little more information - but basically.  Backup your important data to some external device (usb stick).  Insert the medium you used to install 16.04 (dvd or usb stick) and boot pc to that medium - choose the **Try Ubuntu** option.  Once the Desktop is loaded run Gparted - this is a graphic application that will allow you to resize your partition.  That is the principle - however, we need a little more info first.   Install Gparted on your 16.04 install (sudo apt-get install gparted) and post here some pictures of your current partition(s).

---

### Post by yodayams on 2016-11-30
> **Quarkrad said:**
> Would help to have a little more information - but basically.  Backup your important data to some external device (usb stick).  Insert the medium you used to install 16.04 (dvd or usb stick) and boot pc to that medium - choose the **Try Ubuntu** option.  Once the Desktop is loaded run Gparted - this is a graphic application that will allow you to resize your partition.  That is the principle - however, we need a little more info first.   Install Gparted on your 16.04 install (sudo apt-get install gparted) and post here some pictures of your current partition(s).

How can I make a screenshot in Ubuntu?

Zach

---

### Post by howefield on 2016-11-30
> **yodayams said:**
> How can I make a screenshot in Ubuntu?

Open the Dash and search for screenshot.

---

### Post by yodayams on 2016-11-30
Here is the screenshot!

Zach

---

### Post by yancek on 2016-11-30
So which partition do you want to shrink?  sda3 and sda5 look like the only realistic options.  Use the instructions above for GParted and make sure you unmount the relevant partition first.  Instructions are at the link below for resizing in the GParted Manual.

[http://gparted.org/display-doc.php%3Fname%3Dhelp-manual#gparted-advanced-partition-actions](http://gparted.org/display-doc.php%3Fname%3Dhelp-manual#gparted-advanced-partition-actions)

---

### Post by alexeyn on 2016-12-01
[http://positon.org/resize-an-ext3-ext4-partition](http://positon.org/resize-an-ext3-ext4-partition)
but use
```

 resize2fs -f ...

```
instead of
```

 resize2fs ...

```
and  
Parted's resizepart can be used too.

---

### Post by Mark Phelps on 2016-12-01
Just so you know ...

1) Resizing Linux partitions: you can't do this while the partition is mounted, so you would have to boot from CD or USB to resize the Linux partitions.

2) Resizing Windows partitions: do NOT do this using Linux filesystem tools as that risks corrupting the Windows filesystems, preventing Windows from booting, and making it really HARD to make repairs as there are no Windows filesystem repair utilities that run in Linux that can repair NTFS filesystems.

---

### Post by 1clue on 2016-12-01
An addendum to what Mark Phelps posted:

You CAN resize lvm  volumes on-the-fly. If you make a minimal root partition and then  dedicate most of the rest of your drive to lvm2 then you can resize  without slowing down.

I've been doing this for years. The general  idea is that you keep your 'partitions' (logical volumes) fairly small.  If you're doing something that eats up space then you can leave that  running and resize your volume on the fly.

---

