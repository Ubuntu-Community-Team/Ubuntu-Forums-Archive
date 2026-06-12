---
title: "Mounted drive problem"
date: 2008-01-28
forum: General Help
---

### Post by whaase on 2008-01-28
Ubuntu is mounting my second NTFS drive in my system (which is good) but I can not write to it. How can I change it so i as a user can write to that drive? I dont see it in the fstab to change the settings?

---

### Post by taurus on 2008-01-28
You probably need to unmount it first and then mount it with ntfs-3g so you can write to it.  What is the name of the device?

```
df -h
```

---

### Post by whaase on 2008-01-28
Device is hdb1

But where is it currently mounting it from? Its doing it automatically, and there is no entry in the fstab?

---

### Post by taurus on 2008-01-28
Only if you ran the command in my previous post, you would have found out where /dev/hdb1 was mounted to.

Meanwhile, try

```
sudo umount /dev/hdb1
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/hdb1
sudo mount -t ntfs-3g /dev/hdb1 /media/hdb1
ls -la /media/hdb1
```

---

### Post by whaase on 2008-01-28
> **taurus said:**
> Only if you ran the command in my previous post, you would have found out where /dev/hdb1 was mounted to.

Meanwhile, try

```
sudo umount /dev/hdb1
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/hdb1
sudo mount -t ntfs-3g /dev/hdb1 /media/hdb1
ls -la /media/hdb1
```

Its being mounted to /media/media (Thats the drive name)

I think Im asking my question the wrong way. Ubuntu is auto mounting this drive for me. It shows up on my desktop. What file could I modify that has this mount config in it? I always thought fstab did the drive mounting? 

I&#314;l try the way you showed me, but Id like it to mount this way everytime I boot up. :)

---

### Post by whaase on 2008-01-28
> **taurus said:**
> Only if you ran the command in my previous post, you would have found out where /dev/hdb1 was mounted to.

Meanwhile, try

```
sudo umount /dev/hdb1
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/hdb1
sudo mount -t ntfs-3g /dev/hdb1 /media/hdb1
ls -la /media/hdb1
```

When I tried mounting it I got this:

> $LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/hdb1': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.


---

### Post by taurus on 2008-01-28
Sounds like you need to boot up windows and shut it down cleanly instead of putting it into hibernation or sleep mode.

---

### Post by whaase on 2008-01-28
> **taurus said:**
> Sounds like you need to boot up windows and shut it down cleanly instead of putting it into hibernation or sleep mode.

Damn Vista, I just got it, I didnt realize that pressing the red button on the start menu put the computer into hibernation :mad:

Ok, I mounted it the way you showed me, all it working now. How do I make it auto mount that way all the time?

---

