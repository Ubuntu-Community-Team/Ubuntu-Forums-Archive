---
title: "Unable to view windows properly"
date: 2014-01-21
forum: General Help
---

### Post by rmcellig on 2014-01-21
I am running Xubuntu 12.04. For some reason I am not seeing the complete Thunar window (Close box, zoom box etc...), and can't remember how to reset it so the windows look normal. When I go to my Settings Windows Manager or Windows Manager tweaks, nothing at all shows up. 

Might there be a config or setting file that I can delete so that I can access those two settings as well?

What is my best course of action?

Thanks!!

---

### Post by Toz on 2014-01-21
Sounds like the window manager has crashed. Try running the following command from a terminal window:
```
xfwm4 --replace
```
...and see if it comes back.

If it does you should probably clear out your sessions cache as well to prevent if from recurring on next login. To do so:
1. Log out
2. Go to the first virtual console (Ctrl+Alt+F1)
3. Login to that text console
4. Run:
```
cd .cache
rm -rf sessions
```
5. Return to the gui console (Ctrl+Alt+F7)
6. Log in and test.

---

