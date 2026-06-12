---
title: "system updates not working at the moment?"
date: 2013-07-12
forum: General Help
---

### Post by rmcknight on 2013-07-12
Im getting:
Service unavailable [IP: 202.158.214.106 80]

Is anyone else getting this?

---

### Post by gifford on 2013-07-12
No, I do not have the problem. 
What version of Ubuntu are you using?
What server? 
The main server is working so am unsure if you are using US server or another one.

---

### Post by rmcknight on 2013-07-12
im 13.04
i was on the default australian server, you gave me an idea, i swapped to another mirror and its all good.   thanks for the idea.

---

### Post by David006 on 2013-07-12
It looks like **mirror.AARNet.edu.au** (202.158.214.106) is currently down (or routing disrupted).

I replaced default mirror (for AU) with Optus mirror:

> sudo perl -p -i.orig -e 's/au.archive.ubuntu.com/mirror.optus.net/' /etc/apt/sources.list


This fixes for 13.04, 12.04, 12.04 server ..

---

