---
title: "xscreensaver performance"
date: 2007-02-15
forum: General Help
---

### Post by n_hendrick on 2007-02-15
okay I just install xscreensaver and have it loading on login but its performing way slower than gnome-screensaver is. Is there a way to improve the performance of xscreensaver?

---

### Post by dcstar on 2007-02-15
> **n_hendrick said:**
> okay I just install xscreensaver and have it loading on login but its performing way slower than gnome-screensaver is. Is there a way to improve the performance of xscreensaver?

Is hardware acceleration enabled for your video card?
```
glxinfo | fgrep direct
```

---

