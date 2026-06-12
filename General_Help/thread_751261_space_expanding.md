---
title: "space expanding"
date: 2008-04-10
forum: General Help
---

### Post by kingkong22 on 2008-04-10
After I updated some software, my system seems full. see the list below by gparted

partition         filesystem         mountpoint      size           used            unused
/dev/sda1        ntfs                 /media/sda1    224.6 GB   107.4 GB      117.2 GB

/dev/sda2       linux-swap                              486.3MiB     ----              ----
/dev/sda3       ext3                   /                   6.61  GB    6.61 GB        2.84 MiB

unallocated    unallocated                              1.2   GB

How can I get unallocated 1.2 GB space for my ubuntu ? what commands can I use ?
Thanks a lot.

---

### Post by mali2297 on 2008-04-10
First of all, backup all data that is dear to you.

You need to run GParted or some other partition manager from a Live CD, for example, the Ubuntu Install CD. Then you should be able to resize the partition, here is [a guide]("http://gparted.sourceforge.net/larry/resize/resizing.htm").

---

### Post by kingkong22 on 2008-04-10
great! thank you so much !

---

### Post by kingkong22 on 2008-04-10
Hi, Martin

As I highlighted the row unallocated of 1.2 GB then I selected partition menu, I saw resize/move option was disable. maybe I did wrong. Could you give me more in details instructions for appending thoes 1.2 GB to ext3 so that I have more spaces on my ubuntu.
many thanks.

---

### Post by mali2297 on 2008-04-10
You should select the partition that you want to grow, in your case /dev/sda3, then go to the Partition menu. Make sure that the partition is unmounted (no padlock).

---

### Post by kingkong22 on 2008-04-10
Hi, Martin
  When I highlight /dev/sda3 and select partition menu, only three options are enabled :
Unmount
Manage flags
information

other options are disable under partition menu

so, what are the following operations I can do ? thanks a lot.

---

### Post by mali2297 on 2008-04-10
Choose to unmount first. 

It might happen that you have an automount feature that you need to disable. If you use the Ubuntu CD, you can do that through **System --> Preferences --> Removable Drives and Media**.

Also, you can clear some of the used space on your Ubuntu partition with
```

sudo apt-get clean

```
 This should be done when you're running your regular Ubuntu system. It will remove deb-files that has been downloaded by apt-get/Synaptic.

---

