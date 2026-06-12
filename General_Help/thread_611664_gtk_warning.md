---
title: "gtk warning"
date: 2007-11-13
forum: General Help
---

### Post by bratliff on 2007-11-13
gksu gedit /etc/environment
(gksu:11994): Gtk-WARNING **: cannot open display:

Another problem.

---

### Post by mcduck on 2007-11-13
Are you trying this from desktop or from console? Both gksu and gedit are graphical programs and need a running desktop to work. In console, use 'sudo nano /etc/environment' instead..

---

