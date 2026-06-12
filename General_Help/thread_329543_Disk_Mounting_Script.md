---
title: "Disk Mounting Script"
date: 2007-01-01
forum: General Help
---

### Post by Justin Holt on 2007-01-01
I know that on the wiki that if you searched for "mount" it would pull up this entry that had the disk mounting script.  I used it to mount ntfs drives to recover them for friends and now its dissappeared, does anyone know where i can get it if it still exists, or know a similar way (and by similar i mean easy) to do this. Thanks alot.

---

### Post by taurus on 2007-01-01
What's the device of that ntfs drive?  Assuming it's called /dev/hdb1, mount it from a terminal with

Applications -> Accessories -> Terminal
```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/hdb1 /media/windows -o nls=utf8,umask=0222
df -h
```

---

### Post by Justin Holt on 2007-01-01
How do i find its location?

---

### Post by taurus on 2007-01-01
Applications -> Accessories -> Terminal
```
sudo fdisk -l
(assuming that you have the drive plugged in first...)
```

---

### Post by Justin Holt on 2007-01-01
i should hope the hard drive is plugged in, its on a laptop running the live cd ;)

---

### Post by taurus on 2007-01-01
What's the output of that command then?

```
sudo fdisk -l
```

---

