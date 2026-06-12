---
title: "[SOLVED] Usplash"
date: 2008-04-07
forum: General Help
---

### Post by Fate Reconciled on 2008-04-07
I'm trying to optimize the boot process as much as possible. So would disabling Usplash actually speed up the boot process at all? If so would there be significance of 1-2s at least? And is there a safer way than messing with the rc*.d files? I've had quite a few bad experiences with those... 

So far, bootchart maps the entire process out to about 26s total.

---

### Post by SOULRiDER on 2008-04-07
Removing the splash screen could speed things up a little. Just edit
```
/boot/grub/menu.lst
``` and remove "splash" from your kernels parameters.

---

### Post by Fate Reconciled on 2008-04-07
Nice. Cut it down to 24s. Problem solved and a thanks to you.

---

