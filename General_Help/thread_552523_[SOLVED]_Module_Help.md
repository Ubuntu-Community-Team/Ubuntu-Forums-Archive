---
title: "[SOLVED] Module Help"
date: 2007-09-16
forum: General Help
---

### Post by MrFSL on 2007-09-16
I have the following modules that automatically loaded for me at boot time:

lirc_dev
lirc_imon
lirc_i2c

I need them to be loaded in the following order every time:

1) lirc_dev
2) lirc_i2c
3) lirc_imon

Anyone know how I accomplish this?

---

### Post by Ashrael on 2007-09-16
You know about /etc/modules ? open this file and, in order that you want to load, add the modules... that easy...

greetz!

---

### Post by MrFSL on 2007-09-16
Yeah I tried that already... no luck.

---

### Post by MrFSL on 2007-09-16
Alrighty, It appears that lirc_imon is loaded prior to lirc_i2c because it is detected prior to the other at boot up.

So, how do I tell lirc to use /dev/lirc1 for my remote instead of /dev/lirc0 ?

---

### Post by Ashrael on 2007-09-16
is'nt there a .lirc file somewhere to configure?

---

### Post by MrFSL on 2007-09-16
This always happens. I get stuck, I give up, I post a question on this forum, I immediatly find the answer:

From:
[https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy)

```
#/etc/lirc/hardware.conf
LIRCD_ARGS="--device=/dev/lirc0"
LOAD_MODULES=true
MODULES="lirc_dev lirc_i2c lirc_imon"
```

---

### Post by Ashrael on 2007-09-16
Hasta la victoria siempre!:)

---

