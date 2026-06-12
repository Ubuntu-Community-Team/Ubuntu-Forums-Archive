---
title: "Problems with X on LiveCD"
date: 2005-10-29
forum: General Help
---

### Post by AndrewJohnson on 2005-10-29
I've been trying to get the Ubuntu 5.10 LiveCD to boot, but it always gets stuck trying to load X.  The error message is:

```
Fatal server error:
Cannot run in framebuffer mode. Please specify busIDs        for all framebuffer devices
```

I grabbed the log file, and have attached it here, but am not sure how to interpret it.  I have an old nVidia GeForce2 type video card, if it matters.  Any ideas?

---

### Post by audax321 on 2005-10-29
Could you post your /etc/X11/xorg.conf as well. If you can log into a text-based terminal, try:

sudo nano /etc/X11/xorg.conf

go down to Section "Device" and find the driver section and change it to: vesa
It might say nv right now.

Then CNTRL+X and save it. 

When you're back at the prompt, type startx and see if it works then. I've had problems on nVidia cards before where the nv driver doesn't work and I needed to use vesa. Once you get Ubuntu running you can install the correct nVidia drivers from the repos.

---

### Post by AndrewJohnson on 2005-10-29
Thanks.  I tried disabling the framebuffer via the boot parameter on a hunch, and strangely enough that made the framebuffer work.  Go figure.

---

