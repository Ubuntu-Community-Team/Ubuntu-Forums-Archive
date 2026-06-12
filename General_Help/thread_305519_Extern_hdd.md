---
title: "Extern hdd?"
date: 2006-11-23
forum: General Help
---

### Post by haxer on 2006-11-23
Hello ive recently bought an extern hdd cabinet to my 2.5" 20gb hdd and when i plug it in i find my labtops file system that was an windows xp installation .. how do i format it to fat 32? cant rightclick on it

---

### Post by taurus on 2006-11-23
You can do that in Ubuntu but first you need to install gparted and then you need to unmount the drive since you can't format it while it's mounted...

```
sudo aptitude update
sudo aptitude gparted
```

---

### Post by haxer on 2006-11-23
How to unmount usb exter hdd?

---

### Post by taurus on 2006-11-23
Look for the mount point with this command, df -h, and unmount it.  For now, I assume it's called /media/share so you would do 

```
sudo umount /media/share
```
to unmount it.

---

### Post by haxer on 2006-11-23
Thanks i will try it out :)

---

