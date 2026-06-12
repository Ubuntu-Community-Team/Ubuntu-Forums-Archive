---
title: "A test for someone interested"
date: 2008-03-05
forum: General Help
---

### Post by joereith on 2008-03-05
Ok so I wrote over my /media folder trying to automount my second hard drive because I named it media. So now I can't access my second hard drive what do I do?

---

### Post by murataht on 2008-03-05
fix the fstab!
but I don't know how it works with autmounting?

---

### Post by Rocket2DMn on 2008-03-05
Wouldn't it have automounted the hard drive at /media/media then?
Is the hard drive internal or external?  Please post the output of these commands:
```
cat /etc/fstab
sudo fdisk -l
```

---

