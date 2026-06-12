---
title: "can't run mozilla in remote machine"
date: 2007-05-15
forum: General Help
---

### Post by mostafa on 2007-05-15
Hi,

I connect to my remote count using ssh no problem, but when I run mozilla I get the error message

(mozilla-bin:24597): Gtk-WARNING **: cannot open display:

Please what's wrong

---

### Post by aroch1 on 2007-05-21
Try

```
ssh -X SERVER
```

this should enable X forwarding, which I do not believe is enabled by default for most ssh clients.

---

