---
title: "[SOLVED] Pidgin SSL error"
date: 2008-02-13
forum: General Help
---

### Post by James- on 2008-02-13
You've probably heard this 10000 times but I can not longer connect to msn for some reason... I use to be able to but now pidgin went on the fritz(the original one with the 7.10 Gutsy)

Please help says I need SSL!!
> 

SSL support is needed for MSN. Please install a supported SSL library.

Pidgin will not attempt to reconnect the account until you correct the error and re-enable the account.

---

### Post by Ek0nomik on 2008-02-13
> **James- said:**
> You've probably heard this 10000 times but I can not longer connect to msn for some reason... I use to be able to but now pidgin went on the fritz(the original one with the 7.10 Gutsy)

Please help says I need SSL!!

I'd try this:

```
sudo apt-get install libnss-dev libnspr-dev
```

---

### Post by James- on 2008-02-13
> 
sudo apt-get install libnss-dev libnspr-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libnss-dev

doesn't work

---

### Post by James- on 2008-02-13
anyone know why I can't find these?

---

### Post by apetresc on 2008-02-13
Make sure you have the Universe repository (and, failing that, the Multiverse repository) enabled. These packages will certainly solve your Pidgin problem.

---

### Post by James- on 2008-02-15
fixed it by removing the old pidgin(only pidgin(complete removal) downloaded the 2.3.1 source, extracted, compiled(./configure  ; make ; sudo make checkinstall) and it worked for some reason...

---

