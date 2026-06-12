---
title: "Rename Volume ID of ISO File 14.04.3"
date: 2015-12-13
forum: General Help
---

### Post by coljohnhannibalsmith on 2015-12-13
Hello,

Can someone explain to me how to change the volume id of an .iso file?

Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2015-12-15
bump

---

### Post by sudodus on 2015-12-15
The file system, ISO 9660, is read-only, so if you want to tamper with it, you need to work at a low level with some kind of binary editor. I suggest that you avoid writing outside the current character string. If you find no other tool, you can probably do it with ***dd***.

(I would not bother to do it.)

---

