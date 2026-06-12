---
title: "SD card becomes read only after sleep."
date: 2015-09-06
forum: General Help
---

### Post by T-Keith on 2015-09-06
I'm using an SD card for my 3d printer and with works fine until the computer goes to sleep.  I always use eject before pulling the card and it works fine several times, but after sleep it becomes read only after putting the cart back in.   Restarting the computer fixes it again.


thanks,

---

### Post by tgalati4 on 2015-09-06
Look through *dmesg* for SD card errors.  Open a terminal.

```
dmesg | more
```

Spacebar to page forward, "q" to quit.

Post only SD-related errors, not the entire *dmesg* output.

---

