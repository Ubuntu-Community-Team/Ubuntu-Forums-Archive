---
title: "system program problem detected Ubuntu Server 12.04(32bit) after installing ubuntu de"
date: 2013-04-12
forum: General Help
---

### Post by devosli on 2013-04-12
After installing the GUI on Ubuntu Server 12.04 LTS, i got an error 
**system program problem detected**

After many searches in many Forums i only found how to disable this error, but it's not what i'm looking for, i would like to resolve this error and not disable it.

Thanks for advance

---

### Post by devosli on 2013-04-12
I tried this :
[COLOR=#ff8c00]**sudo rm /var/crash/***[/COLOR]
and it work fine right now

---

### Post by lukeiamyourfather on 2013-04-12
There's a left over log file that indicates there was a problem previously. Remove the problematic log and the dialog won't come up anymore.

```
sudo rm /var/crash/*
```

---

### Post by devosli on 2013-04-12
really!!
but what should i do ?

---

