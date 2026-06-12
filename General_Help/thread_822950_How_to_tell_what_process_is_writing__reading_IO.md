---
title: "How to tell what process is writing / reading IO"
date: 2008-06-08
forum: General Help
---

### Post by ayapejian on 2008-06-08
I'm running into a problem where some process is accessing quite a bit of IO and this is slowing down my system to a crawl.  I suspect that it has something to do with firefox, but I would like to find a tool to verify this. 

Does anyone know if theres a way to track exactly what processes are writing IO and how much?  Kind of like 'top' for IO?  Tried searching all over and I couldn't find anything for linux (although I know solaris and windows (via sysinternals) has these tools).

Thanks!

---

### Post by crispinb on 2008-06-08
I had similar needs recently and found iotop: [http://guichaz.free.fr/iotop/](http://guichaz.free.fr/iotop/)

It doesn't need installing if you only have a one-off use for it. Just unpack and run iotop.py in the top-level dir.

---

### Post by ayapejian on 2008-06-08
> **crispinb said:**
> I had similar needs recently and found iotop: [http://guichaz.free.fr/iotop/](http://guichaz.free.fr/iotop/)

It doesn't need installing if you only have a one-off use for it. Just unpack and run iotop.py in the top-level dir.

Perfect, seems to work great.  Thank you!

---

