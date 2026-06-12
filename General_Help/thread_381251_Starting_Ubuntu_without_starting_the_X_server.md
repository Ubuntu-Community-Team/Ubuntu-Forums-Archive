---
title: "Starting Ubuntu without starting the X server"
date: 2007-03-10
forum: General Help
---

### Post by Portable_Jim on 2007-03-10
I am running Edgy and am wondering whether it is possible to start ubuntu normally, except that the X server is not started (desktop edition not server edition). I only want to start it up without X every now and again.

Does anyone know how to do it?

( I know it is a weird request, but please just give me the answer of (or ask questions so you can help me) how to do it, not ask me why I want to do it.)

Thanks
Portable_Jim

Answer: start normally then kill gdm
```
sudo killall gdm
```

---

### Post by strabes on 2007-03-10
On the grub menu, the option below the default one is something like "safe mode," and it boots directly into a root terminal with no bootsplash or anything.

---

### Post by Portable_Jim on 2007-03-10
> **strabes said:**
> On the grub menu, the option below the default one is something like "safe mode," and it boots directly into a root terminal with no bootsplash or anything.

Thanks. However I would like it to be a "normal" boot up, except the X server.

---

