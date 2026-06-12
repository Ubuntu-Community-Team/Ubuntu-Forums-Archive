---
title: "3D driver?"
date: 2007-02-03
forum: General Help
---

### Post by LinuxforHumans on 2007-02-03
I just installed Beryl, but for some reason I keep seeing this message in terminal...

```
libGL warning: 3D driver claims to not support visual 0x4b
```

could someone tell me what this means, and how I might fix it?

---

### Post by dexter on 2007-02-03
I found this on google:
[http://www.mail-archive.com/dri-devel@lists.sourceforge.net/msg28133.html](http://www.mail-archive.com/dri-devel@lists.sourceforge.net/msg28133.html)

Remember that beryl is still beta software.

---

### Post by shironeko on 2007-02-03
I get the same for every 3D aplication I start.

---

### Post by LinuxforHumans on 2007-02-03
Is there any way to fix it?

---

### Post by DarkN00b on 2007-02-03
THis is a hardware limitation. It means your hardware cannot display TrueColor / 32 planes or higher.

---

### Post by igknighted on 2007-02-03
Basically, what they are saying is ignore this warning, as it doesn't affect anything.

---

### Post by DarkN00b on 2007-02-03
Yep. It has no discernible effect on my display. Beryl works perfectly, with the exception of water effects - which are not supported by my Intel graphics chipset.

---

