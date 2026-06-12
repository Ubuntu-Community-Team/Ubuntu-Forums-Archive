---
title: "Automatic update error"
date: 2007-06-22
forum: General Help
---

### Post by pjalegria on 2007-06-22
Hi

I have this error on automatic updates :

ERROR:Opening the cache (E:Read error - read (5 Input/output error), E:the package lists or status file could not be parsed or opened,)

and i cant fix it, can someone help me...:(

tankyou

---

### Post by bapoumba on 2007-06-23
Could you please open a terminal (> Applications > Terminal) and paste the complete error message you get to:
```
sudo aptitude update
```
and your sources.list:
```
cat /etc/apt/sources.list
```

---

