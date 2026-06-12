---
title: "s3 unichrome driver questions/compiz/bery"
date: 2006-11-08
forum: General Help
---

### Post by searayman on 2006-11-08
I read this forum post [http://ubuntuforums.org/showthread.php?t=76037]("http://ubuntuforums.org/showthread.php?t=76037")

and it talks about installing drivers for the s3unichrome, if i install those would beryl and or compiz work for me? If so how can i do this on edgy?

---

### Post by searayman on 2006-11-22
any ideas?

---

### Post by ninevoltz on 2007-01-14
AFAIK the unichrome drivers don't have support for non power of twos textures, so no, I don't think it will work.

---

### Post by DaneDog on 2007-01-19
Compiz Shoutld work... here's a walkthrough... works for me on edgy with openchrome drivers [http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy/](http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy/)

---

### Post by dcstar on 2007-01-19
> **searayman said:**
> I read this forum post [http://ubuntuforums.org/showthread.php?t=76037]("http://ubuntuforums.org/showthread.php?t=76037")

and it talks about installing drivers for the s3unichrome, if i install those would beryl and or compiz work for me? If so how can i do this on edgy?

S3 Unichrome are built into the current Edgy kernel, do:
```
glxinfo
```
to see if they work on your system.

---

