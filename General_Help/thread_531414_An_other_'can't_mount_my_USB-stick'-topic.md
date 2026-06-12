---
title: "An other 'can't mount my USB-stick'-topic"
date: 2007-08-21
forum: General Help
---

### Post by Martje_001 on 2007-08-21
Hi,
Ubuntu (or gnome?) doesn't reconize my USB-stick :(. However, I can mount it with '*sudo mount -t vfat /dev/sda1 /media/sda1*'. Can I reset this somehow?

btw: I'm using Gutsy fully updated!

---

### Post by astralsin on 2007-08-21
hal/dbus should take care of that.  you could always stick a line in your /etc/fstab for it though

```
/dev/sdb1        /media/sdb1  vfat    rw,user,noauto  0       0
```

---

### Post by Martje_001 on 2007-08-22
Why sd**b**?
Thank you very much!

---

