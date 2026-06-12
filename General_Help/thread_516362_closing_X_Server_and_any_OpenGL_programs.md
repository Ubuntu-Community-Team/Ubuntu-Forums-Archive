---
title: "closing X Server and any OpenGL programs?"
date: 2007-08-03
forum: General Help
---

### Post by karl_eller on 2007-08-03
Ok, so I'm going to install the nVidia drivers from nVidia's website, and going through the read-me, it says I need to exit X Server and close any OpenGL programs.

How do I do this? Is it just logging out and then hitting Alt+F1 (or is it Ctrl+Alt+F1?) or is there a console command I need to do? Or do I boot into recovery mode?

Eller

---

### Post by 505 on 2007-08-03
Switching to a TTY (Ctrl+Alt+F1) does not close X. It is still running under Crtl+Alt+F7. To kill X, go to the TTY, log in and type:
```
sudo /etc/init.d/gdm stop
```
Then you can install nVidia drivers. To start X again, use the same code, exept with the command 'start'

---

### Post by karl_eller on 2007-08-03
Sweet, that worked for me.

Thanks

Eller

---

