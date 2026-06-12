---
title: "Avoiding multiple instances of Scite?"
date: 2005-04-22
forum: General Help
---

### Post by Eproxus on 2005-04-22
Is there a way to avoid Scite opening multiple instances, and instead add opened files to the tabbar as Gedit does?

Thanks in advance.

(Btw I'm using Rox as filebrowser, if that is any help)

/ Adam

---

### Post by soce_32 on 2005-04-22
Edit /usr/share/scite/SciTEGlobal.properties, and uncomment #buffers=10, and that should do it.

---

### Post by Eproxus on 2005-04-23
Well, it is already uncommented so that does not help, sorry.

---

### Post by soce_32 on 2005-04-23
Try uncommenting check.if.already.open=1.

That works from xffm4.

---

### Post by Eproxus on 2005-04-23
That solved it! Many thanks!

---

