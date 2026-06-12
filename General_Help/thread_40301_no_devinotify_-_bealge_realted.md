---
title: "no /dev/inotify - bealge realted"
date: 2005-06-08
forum: General Help
---

### Post by puccaso on 2005-06-08
i dont have a /dev/inotify.

the beaglewiki says that hoary kernel has inotify patch 
but there isnt a /dev/notify

i do
```
cat /sys/class/misc/inotify/dev
``` 
and i get nothing, cos misc/inofity doesnt exist..


i do a unname -a and i get
```
Linux jt 2.6.10-5-386 #1 Fri May 20 13:52:48 UTC 2005 i686 GNU/Linux
``` 

so what hoary version has inotify built in?

---

### Post by jdong on 2005-06-08
Don't post questions in the Tips & Customizations forum.

As far as your issue, inotify isn't really required for Hoary to function. IIRC, inotify was dropped late in Hoary development because of strange kernel bugs.

---

