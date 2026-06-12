---
title: "Restarting GNOME leads to being unable to unlock desktop"
date: 2018-05-01
forum: General Help
---

### Post by oxEz on 2018-05-01
Hi.

Running 18.04,  gnome-shell.

If I run ```
gnome-shell --replace &
```, and then lock my screen, I can't unlock it. It's as if something kept pressing "Enter" every second, shows "Authentication Error". 

I can't type my password. I have to stop gdm3 and kill gdm processes and restart it. How can I prevent this from happening?

The reason I run ```
gnome-shell --replace &
``` is because typing ```
r
``` in the ALT-F2 prompt gives me "command not found". That's another issue I think apparently this is supposed to work..

---

