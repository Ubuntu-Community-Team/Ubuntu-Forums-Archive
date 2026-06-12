---
title: "where can i locate the apxs file?"
date: 2007-04-28
forum: General Help
---

### Post by heyo on 2007-04-28
hi, i'm trying to install mod_perl on my local websserver in an attempt to get my cgi-bin directory working.

The installation is asking for the apache apxs file but I cant find it in any of the apache/bin folders.

---

### Post by heyo on 2007-04-28
also my apache was installed as part from ubuntu server edition 6.06, if that helps

---

### Post by K.Mandla on 2007-04-28
I have no experience with mod_perl or apache, but you could ...

```
find / -iname "*apxs*"
```
Is that any help?

---

### Post by heyo on 2007-04-28
thanks yeh that helped.. but turns out that i dont have that file on my system :(

---

