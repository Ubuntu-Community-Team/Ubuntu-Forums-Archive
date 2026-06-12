---
title: "Can't change my shells"
date: 2014-05-21
forum: General Help
---

### Post by gijs2 on 2014-05-21
Hi,

I think there is a problem with my unity 2d since I cannot change my shells in the login screen of ubuntu.
Hopefully someone can help me with this problem, thanks :)

---

### Post by hyperreal on 2014-05-22
What do you mean by "shells"?  Do you mean desktop environment options?

If your hardware is incapable of running Unity 3D, Ubuntu will detect this during installation.   If that is the case, you will only have 2D installed, so the reason you can't select desktop options at the login screen is because there are no other options installed on your system.

---

### Post by grumblebum2 on 2014-05-22
unity 2d hasn't been available since 12.04.
If you don't have the graphics capable of running unity 3D version install the gnome-session-flashback session.
```
sudo apt-get install gnome-session-flashback
```

and log in to the **Gnome Flashback (Metacity)** session.

---

