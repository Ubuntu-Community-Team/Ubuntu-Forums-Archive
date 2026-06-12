---
title: "external hard drive problems"
date: 2007-06-10
forum: General Help
---

### Post by xGutsAndGloryx on 2007-06-10
i am trying to save information to my external hard drive... it gives me this error... Error while copying to "/media/Ext...hippuuden".... what should i do?

---

### Post by taurus on 2007-06-10
What filesystem is that external harddrive?

---

### Post by tpg on 2007-06-10
Does it fail to copy anything, or is it just a few files that don't copy? In the latter case, it could be that the path to those files contains characters not permitted by the filesystem on your external drive.

---

### Post by xGutsAndGloryx on 2007-06-10
its a ntfs hard drive... it reads everything fine but i can't write to it

---

### Post by taurus on 2007-06-10
You need to install and use ntfs-3g if you want to write to ntfs filesystem.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install ntfs-3g
```
Now, unmount that external harddrive and remount it with ntfs-3g driver.

---

### Post by OttifantSir on 2007-06-11
How do you unmount a drive that can't be written to?

Is there anything else to be done to allow writing/deleting of an NTFS drive (or two + a partition on internal HD)?

---

### Post by taurus on 2007-06-11
You can unmount it with

```
sudo umount /dev/sda1
```
_assuming_ /dev/sda1 is the one you want to unmount.  Then, remount it with ntfs-3g this time.

```
sudo mkdir /media/sda1
sudo mount -t ntfs-3g /dev/sda1 /media/sda1
ls -la /media/
```

---

### Post by ry4n on 2007-08-15
taurus : thank you so much for this post i finally got my hardrive to work with your help. Thank you

---

