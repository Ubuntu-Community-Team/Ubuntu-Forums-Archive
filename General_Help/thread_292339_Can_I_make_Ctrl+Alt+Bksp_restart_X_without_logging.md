---
title: "Can I make Ctrl+Alt+Bksp restart X without logging me out?"
date: 2006-11-03
forum: General Help
---

### Post by marinosr on 2006-11-03
Ssia

---

### Post by ~LoKe on 2006-11-03
Well, the X server starts before anything, so I imagine everything running on it (including the login screen) needs to be restarted as well.  As far as I know, what you want is impossible.

---

### Post by LenzM on 2006-11-03
This might work if you boot to the command line, then explicitly startx.  But in the normal course of things I would say this is impossible.

---

### Post by CatKiller on 2006-11-03
I understand that there is a way to start **another** X session for testing things out. I can't remember how to do it, since I never have - just read about it. Might be worth a search as an approach, though.

---

### Post by LenzM on 2006-11-03
> **CatKiller said:**
> I understand that there is a way to start **another** X session for testing things out. I can't remember how to do it, since I never have - just read about it. Might be worth a search as an approach, though.

Go to another tty (press [Ctrl]+[Alt]+{[F1]-[F6]}), login and type ```
startx
```

---

