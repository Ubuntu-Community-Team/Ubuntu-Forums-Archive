---
title: "Gutsy logs out after inactivity"
date: 2007-10-29
forum: General Help
---

### Post by foxylad on 2007-10-29
Hi - 

I have just installed Gutsy on an Inspiron 6400 laptop. After a few minutes of inactivity, it logs out and leaves me at the login screen.

I'm using two screens - the laptop as primary, and a secondary monitor (uses Xinerama under the hood).

The only relevant thing I can find in the log is this:

```
Oct 30 10:39:08 kahu gdm[5533]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
```

Is anyone else having this issue? Any ideas about how to stop it?

Cheers!
Foxylad.

---

### Post by foxylad on 2007-10-31
This turned out to be due to some sort of interaction between OpenGL screensavers and Xinerama. Removing the second screen cured it, as did disabling the screensaver or using a non-OpenGL screensaver.

---

