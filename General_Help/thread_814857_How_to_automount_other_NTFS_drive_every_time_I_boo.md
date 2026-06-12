---
title: "How to automount other NTFS drive every time I boot up my computer"
date: 2008-06-01
forum: General Help
---

### Post by D.Sync on 2008-06-01
As the title stated, whenever I boot up my computer I will need to mount those NTFS drives myself. One of them contain WinVista while other contain WinXP. The 3rd drive, which I installed Ubuntu with, can be automounted.

I'm using Ubuntu 8.04 btw.

---

### Post by pro003 on 2008-06-01
type in terminal

```
sudo apt-get install ntfs-config ntfs-3g
```


then go to Applications > System tools > NTFS.....

---

### Post by D.Sync on 2008-06-01
> **pro003 said:**
> type in terminal

```
sudo apt-get install ntfs-config ntfs-3g
```


then go to Applications > System tools > NTFS.....

That will do it? I try restarting my computer.

---

### Post by ugm6hr on 2008-06-01
> **D.Sync said:**
> That will do it? I try restarting my computer.

A little (but only a little) more than just that...

[http://ubuntuforums.org/showthread.php?t=785263](http://ubuntuforums.org/showthread.php?t=785263)

---

