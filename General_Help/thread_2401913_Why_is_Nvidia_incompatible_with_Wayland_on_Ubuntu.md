---
title: "Why is Nvidia incompatible with Wayland on Ubuntu?"
date: 2018-09-24
forum: General Help
---

### Post by yerbestpal on 2018-09-24
I recently moved from Opensuse back to Ubuntu for various reasons. One thing Opensuse done very well however was, Wayland. It had no issues supporting my Nvidia GTX1050 card while under Wayland. Unfortunately this isn't the case under Ubuntu.

I should mention that I installed the default Gnome session by running:

```
sudo apt install gnome-session
```

And then choosing the non-Xorg session from GDM, I run Wayland. It runs very well, and in particular I am thoroughly enjoying the multi-touch support. Unfortunately it seems to not support the discrete GPU, which is a deal breaker. I have to wonder why this is possible under Opensuse but not Ubuntu, and if it is, could someone point me in the right direction?

Thanks.

---

### Post by idkwhatimdoing1.0 on 2018-09-24
Hi, Nividia and wayland are just simply not compatible. Basically of the wayland creq (intel, AMD and more) are following a path for buffer API (also known as GBM) Nivida has refused to follow this protocol. Nivida is just trying to pursue EGLStreams technology so there drivers won't be compatible. Maybe in the future Nivida will decide to switch.

---

