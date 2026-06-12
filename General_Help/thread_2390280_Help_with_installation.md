---
title: "Help with installation"
date: 2018-04-27
forum: General Help
---

### Post by Manuel_Herrera on 2018-04-27
I am trying to install a software I need.

Terminal shows:

~/SR-TestesUSB-1.0 $ ./SR-TestesUSB
Couldn't load file:/home/w_budge/SR-TestesUSB-1.0/runtime/1.3.1-beta/libtide.so, error: libgcrypt.so.11: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "atk-bridge"

---

### Post by Claus7 on 2018-05-01
Hello,

one of the messages you get is telling you that:
either libgcrypt.so.11 does not exist in your system or 
you have to set the path to that file if it is downloaded somewhere.

So either:
1) you have to install this library (if it is spelled correctly) via synaptic
2) or you have to download it separately and when you try to install the SR-TestesUSB to point to the path that you have placed it.

Regards!

---

