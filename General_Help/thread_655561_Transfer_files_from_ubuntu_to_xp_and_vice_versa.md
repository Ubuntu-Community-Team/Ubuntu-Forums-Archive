---
title: "Transfer files from ubuntu to xp and vice versa"
date: 2008-01-01
forum: General Help
---

### Post by Virgilio on 2008-01-01
I would like to transfer or access certain files on my windows partition(meaning that the files are on the same hard drive but on different partitions) while on Ubuntu  or transfer files from Ubuntu partition while logged into windows .Is this possible if so how?

---

### Post by bigken on 2008-01-01
install [ntfs]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html") config tool in ubuntu 

install [this]("http://www.fs-driver.org/") in windows

---

### Post by ~LoKe on 2008-01-01
Well, I only know a couple ways of doing this, which may not be enough for you.

You can mount the NTFS partition while in ubuntu, and copy files from/to it (I'm not sure if it's yet safe to write to the NTFS partition, but I believe so).  Or...more elegantly..
.```
sudo apt-get install ntfs-config
sudo ntfs-config
```
Follow the steps [here](http://www.filledvoid.com/2007/12/17/how-to-mount-an-ntfs-partition-in-ubuntu/).

And in Window, you can run a program called "explore2fs" to copy files from your ubuntu partition.

---

### Post by KOld Iron on 2008-01-01
Another way would be using a USB stick formatted with FAT32, which can be read both by Linux and Windows. That's the quick and dirty solution :)

---

### Post by Virgilio on 2008-01-03
> **KOld Iron said:**
> Another way would be using a USB stick formatted with FAT32, which can be read both by Linux and Windows. That's the quick and dirty solution :)

That's the first thing i tried before making this thread hehe but i wanted an alternate method so thanks to everybody that contributed to helping me

---

