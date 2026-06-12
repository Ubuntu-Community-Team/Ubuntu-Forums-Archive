---
title: "[SOLVED] messed up badly [permissions]"
date: 2007-08-18
forum: General Help
---

### Post by Firippu on 2007-08-18
i  locked myself outta my own server, i disabled root and i changed the only user permissions with sudo chmod 600 /  i can't use sudo anymore and i don't have access to anything beyond / which is everything! don't ask me why i did this.. :-k is there anyway to fix this without reinstalling? i have Ubuntu Server 7.04

---

### Post by taurus on 2007-08-18
> **Firippu said:**
> i  locked myself outta my own server, i disabled root and i changed the only user permissions with **sudo chmod 600 /**  i can't use sudo anymore and i don't have access to anything beyond / which is everything! don't ask me why i did this.. :-k is there anyway to fix this without reinstalling? i have Ubuntu Server 7.04

Boot into recovery mode from GRUB menu and run

```
chmod 755 /
```
Reboot and see what happens now.

```
shutdown -r now
```

---

### Post by Firippu on 2007-08-19
that worked.. thanks

---

