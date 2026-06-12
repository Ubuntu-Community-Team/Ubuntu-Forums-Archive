---
title: "help to resize ext3 partition"
date: 2007-05-21
forum: General Help
---

### Post by Jesus4life0412 on 2007-05-21
hi

I am a newbie when it comes to Linux. I recently  did a dual boot with  Ubuntu on one hard drive a 200gb  using Ubuntu's install partitioner and the other the 30 gig hard drive has xp pro on it. My problem is Ubuntu used the entire 200 gig for itself and i dont want that much space for Ubuntu.so i tried resizing my ext3 partition using gparted it would not let me how can i resize this partition?

thank you

Louie

---

### Post by pbw on 2007-05-21
Just boot up using a live CD, or ubuntu install cd and you'll be able to resize it no prob (it cant be mounted when you're trying to apply changes).

---

### Post by Jesus4life0412 on 2007-05-21
i have tried that and i also  unmounted using gparted i got an error messag e

---

### Post by Crakie on 2007-05-21
AFAIK ext3 cannot be resized. You could convert it to ext2, resize it and convert it back to ext3, but I don't know how safe that procedure is. I looked into this quite a while ago, so maybe I am talking nonsense. I do remember being shocked that resizing ext3-partitions was not easy as pie.

---

### Post by cotcot on 2007-05-21
Have you seen [this]("http://www.hermann-uwe.de/blog/resizing-ext3-partitions-with-parted") ?

---

### Post by pbw on 2007-05-21
The man page for resize2fs says it resizes ext3,

> 
DESCRIPTION 
 The resize2fs program will resize ext2 or ext3 file systems. It can be used to enlarge or shrink an unmounted file system located on device. If the filesystem is mounted, it can be used to expand the size of the mounted filesystem, assuming the kernel supports on-line resizing. (As of this writing, the Linux 2.6 kernel supports on-line resize for filesystems mounted using ext3 only.).

 though i've never tried it. 

There's also a howtoforge article on steps needed. [http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)

--pbw

---

### Post by Gary.M on 2007-06-17
I have a separate home partition that is Ext3. I resized it with Acronis Disk manager Suite. I don't know about your boot partition though. Only thing with this approach is that you need to buy something, and install it in Windows... OK if you're dual boot though.

---

