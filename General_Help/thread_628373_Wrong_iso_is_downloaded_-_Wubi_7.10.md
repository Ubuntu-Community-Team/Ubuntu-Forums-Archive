---
title: "Wrong iso is downloaded - Wubi 7.10"
date: 2007-12-01
forum: General Help
---

### Post by zarkoff95 on 2007-12-01
Hello,

Used version : Wubi-7.10-alpha-rev386
I choose Ubuntu (same with Kubuntu)...

I've a Intel Core 2 Duo and Wubi is downloading ubuntu-7.10-desktop-amd64.iso instead of ubuntu-desktop-i386.iso

Is there a way to force the download ?

Will it be ok if I rename ubuntu-desktop-i386.iso.metalink to ubuntu-7.10-desktop-amd64.iso.metalink ?

With Wubi-.7.04 it worked fine.

Regards.

---

### Post by shafin on 2007-12-01
ubuntu-7.10-desktop-amd64.iso is the 64 bit version.Since your Core 2 Duo is  capable of 64 bit,wubi has chosen this for you.

---

### Post by ago on 2007-12-03
You can force the 32bit starting wubi with the option "--32bit"

---

