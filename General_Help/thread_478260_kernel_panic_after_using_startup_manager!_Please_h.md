---
title: "kernel panic after using startup manager! Please help!"
date: 2007-06-19
forum: General Help
---

### Post by StevenX on 2007-06-19
EDIT: MANAGED TO FIX IT myself after an hour or so's research..

So I just used start-up manager to change my usplash theme. Upon restarting, I get the error:

```
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)
```

If I replace menu.lst with menu.lst.backup, nothing changes.

However, in the grub bootloader menu I can get back into the kernl by selecting the kernel, pressing e, selecting the 3rd line (with the kernel name), pressing e again, then adding ".bak," to the end of the line, pressing enter and then b to boot, as suggested in another thread.

Presumably there's something wrong with some configuration file somewhere, but as I said I already restored the menu.lst to its pre-SUM state.. so where do I go from here?

---

### Post by Qu4k3R on 2007-06-19
Reboot.
If you are in grub, edit the command line so linux start with your linux partition.

I think you have selected the wrong partition.

---

### Post by StevenX on 2007-06-19
> **Qu4k3R said:**
> Reboot.
If you are in grub, edit the command line so linux start with your linux partition.

I think you have selected the wrong partition.

I managed to fix it myself, by adding the ".bak," to the end of the kernel ref in menu.lst. I then installed some Ubuntu Studio packages which broke it again. Removing the ".bak," solved the problem that time... Seems very strange, but it's all fixed now!

---

