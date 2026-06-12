---
title: "rsync Feisty iso"
date: 2007-05-17
forum: General Help
---

### Post by afljafa on 2007-05-17
I have a beta version of the Feisty iso that I would like to update to current. Does anyone have a rsync location and command I can use to get this done?

Cheers.

---

### Post by afljafa on 2007-05-17
Ok - This seems to work

```
rsync -avzpPv --stats rsync://cdimage.ubuntu.com/cdimage/daily-live/current/feisty-desktop-i386.iso .
```

---

### Post by mdurham on 2007-05-18
thanks for that

---

