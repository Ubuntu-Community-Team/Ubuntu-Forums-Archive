---
title: "NTFS won't mount at login"
date: 2008-06-10
forum: General Help
---

### Post by MongooseCage on 2008-06-10
My ntfs partition won't mount at login.

mount point /media/disk
sda1

I am supposing that there is a command for this like at .profile but i can't find .profile and I don't know what command should i use though i tried 

> sudo mount dev/sda1/media/disk

Please help I really want to save the trouble of going into banshee and having a memory hog before I realized that I forgot to mount the partition.

---

### Post by drs305 on 2008-06-10
To manually mount:
```
sudo mount -t ntfs dev/sda1/ media/disk 
```

Make sure you have created the mount point **/media/disk**.

Install and run **ntfs-config** to set this up to automatically mount at boot.

---

### Post by Gerlads Mod on 2008-06-10
You typed that command wrong. It's actually:
**sudo mount dev/sda1 /media/disk**
Make sure there's a space between the partition and the mount point.
And yes, make sure /media/disk actually exists.

Also, when I mount my HDD I make a folder in the root of the partition or in /mnt called HDD and I mount it there.

---

### Post by MongooseCage on 2008-06-11
awesome, worked out! now no more hanging banshee lol.


[COLOR="Red"]**[SIZE="5"][Thread Solved!][/SIZE]**[/COLOR] I dont know where to mark it solved

---

### Post by Joeb454 on 2008-06-11
It's in thread tools at the top of this page :)

---

