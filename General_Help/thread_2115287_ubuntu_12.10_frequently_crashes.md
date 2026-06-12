---
title: "ubuntu 12.10 frequently crashes"
date: 2013-02-12
forum: General Help
---

### Post by ahmed yosif on 2013-02-12
i have 4gb ram ,dual core processor ,2100 ati radeon graphics
and my ubuntu 12.10 crashes frequently

---

### Post by unheeding on 2013-02-12
What crashes?  Do you get a kernel panic?  If so, you may want to check [this link out](https://wiki.ubuntu.com/Kernel/KernelDebuggingTricks).

Have you tried updating to the latest packages?

---

### Post by ahmed yosif on 2013-02-13
mostly firefox,ubuntu software center ,and home folder.when this happens,the screen fades to black and white. also   message of internal error appears

---

### Post by unheeding on 2013-02-13
> **ahmed yosif said:**
> mostly firefox,ubuntu software center ,and home folder.when this happens,the screen fades to black and white. also   message of internal error appears

The whole screen dims?  Or just the Firefox window? (run it non-maximized to see for sure).

When the message for an internal error pops up, what does it say under details?

Try updating your packages.  If Software Updater won't run, try this in a terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by ahmed yosif on 2013-02-13
sorry the whole system crashed and i formatted the drive

---

### Post by TOMBSTONEV2 on 2013-02-13
Perhaps pt 12. 04 on there, I have had next to no issues with it. It has been a grand os. If not stick with a few minor glitches and hope updates get released soon. :p

---

