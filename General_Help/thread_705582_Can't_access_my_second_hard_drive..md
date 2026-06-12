---
title: "Can't access my second hard drive."
date: 2008-02-23
forum: General Help
---

### Post by Envergure on 2008-02-23
I have two hard drives on my computer, one is 80GB and has Ubuntu installed on it and one is 40GB and had Windows XP Pro.  Just now I finally removed XP Pro for good by formatting the 40GB drive, intending to use it to back stuff up.  I formatted the entire drive as EXT3 but now I can't figure out how to access it.

---

### Post by taurus on 2008-02-23
You need to add an entry in /etc/fstab to have it mount automatically each time you boot.  _Assuming_ it is /dev/sda1 and you want to mount it to /media/storage, open a terminal and edit /etc/fstab

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sda1   /media/storage   ext3   defaults   0   1
```
Save it and close gedit window.  Then, create a new mount point and mount it.

```
sudo mkdir /media/storage
sudo mount -a
df -h
```
Now, if you want to be able to write to it without using sudo/gksudo, then you need to change the ownership of /media/storage from root to your login name, _assuming_ your login name is **john**.

```
sudo chown -R **john**:**john** /media/storage
ls -la /media
```

---

