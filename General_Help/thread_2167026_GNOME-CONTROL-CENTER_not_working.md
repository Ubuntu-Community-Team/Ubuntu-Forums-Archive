---
title: "GNOME-CONTROL-CENTER not working"
date: 2013-08-12
forum: General Help
---

### Post by f0olyc0oly on 2013-08-12
Hi, I'm using an lxde environment from mini.iso but the applet/plugin from the panel are not working like the Display, Power, Volume, etc.

I did the MALLOC_CHECK_=1 gnome-control-center it automatically starts but still not works.

I went to /usr/share/applications and edited some of the .desktop for example **gnome-display-panel.desktop**

I added the **gksu** after the Exec and I managed to get it work. But is there a way for it to work without asking for admin password?

---

### Post by MG&amp;TL on 2013-08-12
I think *GNOME control centre *requires GNOME for parts of it to work. So when you are in LXDE, the control centre do not work, but may be automatically started if you are not root.

How exactly are the applets not working?

---

