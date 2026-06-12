---
title: "Mounting multiple devices (or partitions) on one directory"
date: 2007-07-10
forum: General Help
---

### Post by mayfer on 2007-07-10
Hi,
I was wondering if it is possible to **mount multiple devices onto a single directory**. If it IS possible, does anybody know how to do so, or know of any websites which explain how to do this?

Also, if it can be done, when I write a new file to that directory, how does linux decide which device to write it onto?

Thanks a lot,
- Murat.

---

### Post by marsbt on 2007-07-10
mount multiple devices onto a single directory ......... this is equivalent to pointing towards more than one direction with your finger at the same instant. So you can't do it with one directory. 

However, what you can do is to mount each partition on a different directory  at the same directory level. E.g. say you have /mnt on your system. You can make new directories in /mnt e.g. /mnt/myUSBHDD, /mnt/myUSBKey /mnt/myExtDVDR, etc. and mount each of the devices (USB HDD, USB Key, external DVD writer) to those directories respectively.

---

### Post by EndPerform on 2007-07-10
My question would be: Why?  Why would anyone want to mount multiple devices on the same mountpoint?  The only reason I could think of would be to copy a file to multiple places at once, but that can be done with a simple script or even a copy / paste action through a GUI.  I'm not trying to dissuade you from finding an answer, but if we know what your ultimate goal was, there might be a better alternative.

---

### Post by mayfer on 2007-07-10
Well, say I have two small disks, and I want to take advantage of all the space that I can. If I could mount both disks as, say, the root directory, that would make things easier.

---

### Post by marsbt on 2007-07-10
You could use both the small disks for different tasks but you can't tell the system that those two disks are just one single disk (unless you setup a RAID array - which won't really give you the advantage the way you want though). How about making different partitions for /, /boot, /usr (usually this requires largest space), /home, /var, and swap so that some of them like on disk 1 while others on disk 2. That way you will be *taking advantage* of both disks.

---

### Post by mayfer on 2007-07-10
Alright, so it's not possible afterall =)
Thanks for the help, guys.

---

