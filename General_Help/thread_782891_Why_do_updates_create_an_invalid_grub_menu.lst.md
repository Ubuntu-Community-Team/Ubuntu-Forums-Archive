---
title: "Why do updates create an invalid grub menu.lst?"
date: 2008-05-05
forum: General Help
---

### Post by 01000111 on 2008-05-05
I have 4 partitions on a single 500GB drive.
  (hd0,0) - 10GB NTFS WinXP (can't remember the last time I used it)
  (hd0,1) - 15GB ext3 Ubuntu 8.04
  (hd0,2) - 2GB linux-swap
  (hd0,3) - 439GB ext3 used for all my documents, media, etc

Whenever I update the kernel and the menu.lst file is re-created, the menu.lst points to (hd0,3) which, of course, fails to boot.

Its no effort to change all the (hd0,3) to (hd0,1) in menu.lst, but why isn't it created correctly in the first place?

**  This isn't really a complaint, but rather I'm just pointing out a bit of room for improvement.  **

01000111

---

### Post by warp99 on 2008-05-05
> **01000111 said:**
> I have 4 partitions on a single 500GB drive.
  (hd0,0) - 10GB NTFS WinXP (can't remember the last time I used it)
  (hd0,1) - 15GB ext3 Ubuntu 8.04
  (hd0,2) - 2GB linux-swap
  (hd0,3) - 439GB ext3 used for all my documents, media, etc

Whenever I update the kernel and the menu.lst file is re-created, the menu.lst points to (hd0,3) which, of course, fails to boot.

Its no effort to change all the (hd0,3) to (hd0,1) in menu.lst, but why isn't it created correctly in the first place?

**  This isn't really a complaint, but rather I'm just pointing out a bit of room for improvement.  **

01000111

Do you have the default grub root drive defined? It should look like this:
```
# groot=(hd0,1)
```
Because during kernel updates grub looks for this as the root drive and sets it accordingly.

---

### Post by mali2297 on 2008-05-05
Can you post your menu.lst?

The debian installer stores some default options in it. Perhaps you need to change one of them.

---

### Post by 01000111 on 2008-05-05
> **mali2297 said:**
> Can you post your menu.lst?

The debian installer stores some default options in it. Perhaps you need to change one of them.

My corrected /boot/grub/menu.lst with comments removed.  When auto created this morning after updating the kernel, all (hd0,1) were (hd0,3) and I had to change 'em back.  This also happened when I upgraded from 7.10 to 8.04 the other week.


----------begin menu.lst----------
default		0

timeout		3

color cyan/blue white/blue

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=a3aea310-a67c-40f2-b1a0-e6b523402c35 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=a3aea310-a67c-40f2-b1a0-e6b523402c35 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title ...
root

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a3aea310-a67c-40f2-b1a0-e6b523402c35 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a3aea310-a67c-40f2-b1a0-e6b523402c35 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.24-12-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=a3aea310-a67c-40f2-b1a0-e6b523402c35 ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-12-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=a3aea310-a67c-40f2-b1a0-e6b523402c35 ro single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

title ...
root

title Windows XP
root (hd0,0) 
savedefault
makeactive
chainloader +1
-----------end menu.lst---------

01000111

---

### Post by forestpixie on 2008-05-05
You'll have to post the whole thing not part of it - there are bits needed at  the beginning

---

### Post by mali2297 on 2008-05-05
> **01000111 said:**
> My corrected /boot/grub/menu.lst with **comments removed**.

The comments are important here. Lines with a single # are read by the debian installer when it recreates the list.

---

### Post by bodhi.zazen on 2008-05-05
And lines starting with # in the config section are not comments.

In the config section, lines with ## are comments and # (single #) are your configuration settings.

We need to see the config section, the section with all the ## and #

---

### Post by 01000111 on 2008-05-05
> **bodhi.zazen said:**
> And lines starting with # in the config section are not comments.

In the config section, lines with ## are comments and # (single #) are your configuration settings.

We need to see the config section, the section with all the ## and #

Well, that's good to know.  Thanks.  menu.lst renamed with .txt attached.

01000111

---

### Post by warp99 on 2008-05-05
> **01000111 said:**
> Well, that's good to know.  Thanks.  menu.lst renamed with .txt attached.

01000111

Here's the problem:
```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)
```
Notice something? That should be '# groot=(hd0,1)'. Once you change that your updates will be correctly applied to the proper partition.

---

### Post by mannheim on 2008-05-05
Edit: Deleted. Previous reply does it.

---

### Post by 01000111 on 2008-05-05
> **warp99 said:**
> Here's the problem:
```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)
```
Notice something? That should be '# groot=(hd0,1)'. Once you change that your updates will be correctly applied to the proper partition.

Yep...  right after I was informed that the # are not comments, I saw that as well...  as always, it's easy when you know the answers!!

Thanks all.

01000111

---

