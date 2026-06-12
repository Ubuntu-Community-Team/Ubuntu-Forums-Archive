---
title: "Can't write to USB flash drive"
date: 2008-06-15
forum: General Help
---

### Post by Rhapsody on 2008-06-15
This a simple but frustrating problem. I had a USB flash drive that was formatted as FAT32. I was having some problems with this, so I used QtParted to reformat it as ext3 (the same as all of my partitions), but now neither PC will write to the flash drive at all. Both just give an "Access denied" error. I'm guessing I need to explicitly change the permissions on the flash drive to let me write stuff to it while not in superuser mode, but how?

---

### Post by p_quarles on 2008-06-15
It most likely already has the correct permissions, but you will need to (in superuser mode) change the ownership to your user.

By the way, ext3 isn't a particularly good filesystem for a flash medium. ext2 (not journaled) will extend the life of the drive by comparison.

---

### Post by Rhapsody on 2008-06-15
> **p_quarles said:**
> It most likely already has the correct permissions, but you will need to (in superuser mode) change the ownership to your user.
Unfortunately, I don't have the necessary experience to know how to do that. That's why I made this topic.

> **p_quarles said:**
> By the way, ext3 isn't a particularly good filesystem for a flash medium. ext2 (not journaled) will extend the life of the drive by comparison.
I can reformat it again later if this works, but I'm not all that worried about the lifespan of the drive really. I only purchased it to transfer this data, and I'm eager to finally get it over and done with.

---

### Post by p_quarles on 2008-06-15
> **Rhapsody said:**
> Unfortunately, I don't have the necessary experience to know how to do that. That's why I made this topic.
Okay, that's fine. There are two ways to do this. One is to run your file manager as root:
```
gksu nautilus
```
or (for Xubuntu):
```
gksu thunar
```
or (for Kubuntu):
```
kdesu konqueror
```
Then, find the USB drive, right click on it, and select the field that allows you to change ownership. 

The command line way (just as easy, but requires slightly more familiarity with the file naming conventions) is to figure out the mount point of the drive:
```
df
```
Look for the device mounted under the /media directory, as this will nearly always be the pluggable device. Make the number of bytes contained on the device matches what you were expecting. It will most likely be named something like /media/sdb1. Given that mount point, the command to change ownership to yourself would be:
```
sudo chown -R $(whoami) /media/sbd1
```

> I can reformat it again later if this works, but I'm not all that worried about the lifespan of the drive really. I only purchased it to transfer this data, and I'm eager to finally get it over and done with.
Cool. Don't underestimate the value of a good flash drive, though. There are really more uses than you might think. ;)

---

