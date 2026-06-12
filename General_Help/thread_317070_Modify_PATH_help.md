---
title: "Modify PATH help"
date: 2006-12-11
forum: General Help
---

### Post by Phalangees on 2006-12-11
i need to do this:

```
Make your PATH include :/usr/local/arm-elf/bin
```

but i don't know how. Could someone help me out??

---

### Post by po0f on 2006-12-11
Phalangees,

Open up ~/.bashrc in your editor of choice and add the following line to the bottom:
```
[FONT="Courier New"]PATH="${PATH}:/usr/local/arm-elf/bin"[/FONT]
```

---

### Post by Phalangees on 2006-12-12
thanks a bunch.

---

