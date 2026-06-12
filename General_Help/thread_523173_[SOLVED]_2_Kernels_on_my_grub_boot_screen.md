---
title: "[SOLVED] 2 Kernels on my grub boot screen?"
date: 2007-08-11
forum: General Help
---

### Post by kinngg on 2007-08-11
I have updated my kernel and now on my boot screen i have to kernels to boot, how can i remove it?

---

### Post by Nekiruhs on 2007-08-11
You don't need to. The second is kept in case you break your first one.

---

### Post by ddrichardson on 2007-08-11
But if you do you can remove the entry from /boot/grub/menu.lst - see man grub for more information. Like Nekiruhs says though - its a good policy to keep it available.

---

### Post by kinngg on 2007-08-12
i see thanks

---

