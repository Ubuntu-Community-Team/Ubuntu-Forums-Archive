---
title: "plymouthd crash at startup"
date: 2018-04-12
forum: General Help
---

### Post by Keith_Helms on 2018-04-12
I get this error frequently when booting my system:

[ATTACH=CONFIG]279264[/ATTACH]

Is there any way to fix this?

---

### Post by tripp98 on 2018-04-15
seams to be an on going problem

try this first.

sudo dpkg-reconfigure plymouth

---

### Post by tomdkat on 2018-11-21
> **tripp98 said:**
> seams to be an on going problem

try this first.

sudo dpkg-reconfigure plymouthI'm experiencing this crash on Ubuntu 18.10.  I just ran the dpkg-reconfigure command so we'll see what happens.  :)

Thanks!

Peace...

---

### Post by jerry47 on 2018-11-30
I'm experiencing it on my laptop which I just installed 18.10. But not on my desktop which also has 18.10. I reinstalled plymouth on the laptop no change. Ran that command first and no change. 

Gerald

---

### Post by jerry47 on 2018-11-30
I just installed plymouth-x11 on the laptop and the problem appears fixed. I was also seeing the plymouth boot text screen on startup and shutdown and now I'm not. The desktop as mentioned above does not have the problem with x11 not installed. Is this a laptop issue only? 

Gerald

---

