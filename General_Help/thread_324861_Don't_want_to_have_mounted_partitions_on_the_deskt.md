---
title: "Don't want to have mounted partitions on the desktop"
date: 2006-12-24
forum: General Help
---

### Post by Poka64 on 2006-12-24
Is there a way to not have the mounted partitions on the desktop?

Right now I have my windows partition and my second HDD on the desktop and I don't want that, I just want to have them on my "Places" menu.

---

### Post by taurus on 2006-12-24
You can modify /etc/fstab and mount them somewhere else instead to /media directory...

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
Don't forget to create a new mount point if you change /etc/fstab to something else!!!

---

### Post by meng on 2006-12-24
This thread covers the possible solutions:
[http://ubuntuforums.org/showthread.php?t=223400](http://ubuntuforums.org/showthread.php?t=223400)
1. make all mounts invisible
2. don't auto-mount
3. choose a mountpoint not in /media

---

### Post by Poka64 on 2006-12-24
Thank you so much, I just used the setting in gconf-editor to remove them from the desktop :)

---

### Post by xabbott on 2006-12-24
For anyone else who wants this changed. Run 
> gconf-editor

Go to 
/apps/nautilus/desktop/volumes_visible

---

