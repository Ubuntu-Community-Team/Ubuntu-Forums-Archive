---
title: "Gimp is not launching."
date: 2017-07-09
forum: General Help
---

### Post by jaren2004 on 2017-07-09
Hi i have a problem whenever i open try to open gimp nothing happens. So i tried opening it through the terminal it then gave me this output:
(gimp:6464): GLib-GObject-WARNING **: g_object_set_valist: object class 'GeglConfig' has no property named 'cache-size'


(gimp:6464): Gtk-WARNING **: Unable to locate theme engine in module_path: "clearlooks",
Segmentation fault (core dumped)

Please help me fix this i need Gimp to edit my photos.
Also thanks a lot if you do!

:D

---

### Post by Frogs Hair on 2017-07-09
The warning is theme specific , have tried with another theme ?

> [COLOR=#000000]Unable to locate theme engine in module_path: "clearlooks",[/COLOR]

---

### Post by jaren2004 on 2017-07-09
Ya i did used a dark blue theme

---

### Post by jaren2004 on 2017-07-09
Nvm i actually looked around more for problems simliar to mine it took a while but i apparently just needed to install some slackware thanks for the help anyway even though i kinda wasted your time sorry.

---

### Post by jaren2004 on 2017-07-09
Btw in case anyone finds this thread the slack ware is gegl just install it in the terminal with sudo apt install gegl

---

