---
title: "Uninstalling Ubuntu...kinda"
date: 2006-08-19
forum: General Help
---

### Post by eyebrowman92 on 2006-08-19
So I've got a 40gb HD and a 120gb HD. I had Dual booted with ubuntu and Wundows on the 40gb one. I recently got the 120gb one and installed ubuntu on it. Now, I want only Windows on my 40gb HD. I booted into the livecd and deleted the ubuntu partition, and that worked fine. But I'm having some trouble getting the Windows partition to take up the entire HD. When I go to do this I get an error saying the following operation may effect following operations on list, when there are no following operations on the list. It rescans devices and I'm right back where I'm started, with 20gb of unallocated space. What am I doing wrong?

---

### Post by zxee on 2006-08-19
You didn't say what type of drives you have or how they're connected (ide, sata, master, slave)
But you could use cfdisk from a terminal type sudo cfdisk /dev/hdx
if you have a sata drive it would be sdx and where the 'x' is you have to supply the drive letter. sudo fdisk -l will give you your drive and partition info if you need it.
Once you have the drive open that you want you can try deleting or changing the partition that you want to use for windows. Hope that helps.

Well-thinking about this a little longer if you want to change this partition back to NTFS you might need to use commercial software to do that. I'm not sure.

---

### Post by eyebrowman92 on 2006-08-19
I tried that, doesn't work, and now I can't even boot into Windows.

---

### Post by TheRingmaster on 2006-08-19
why don't you try downloading and burning to disk what is known as Gparted. Here is the website. [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by The Noble on 2006-08-19
Sounds like you need to use something like partition magic. If you are using an Ubuntu live cd to fix your drive, it sounds like a bad idea. Try knoppix, as it actually can read and write ntfs. 

Hopefully you didn't mess your windows partition totally. Maybe the grub got messed?

---

### Post by .t. on 2006-08-19
Woah people: slow down. Don't go doing anything crazy! It really doesn't matter how the drives are connected. What is your drive layout; ie - how is it partitioned? It is possible to resize NTFS (I think) with GParted, and definately FAT32. So post your layout, and we can help better.

---

### Post by zxee on 2006-08-19
> **eyebrowman92 said:**
> I tried that, doesn't work, and now I can't even boot into Windows.

I'm sorry that you're having problems with booting now.
Please explain specifically what you tried. 

I gave you some options to try but I don't know exactly what you did to perhaps lose the ability to boot windows.

---

