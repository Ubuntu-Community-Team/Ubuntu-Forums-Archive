---
title: "command line to invoke text editor to tweak xorg.conf"
date: 2007-09-27
forum: General Help
---

### Post by kommisar on 2007-09-27
I reconfigured my xserver to get a motherboard transplant to work.  Now I need to edit the xorg.conf file to get my mouse wheel working.  What is the command line I can use to invoke a text editor with super user status so I can edit xorg.conf?  I have a vanilla feisty install.

TIA

---

### Post by GoodPanos on 2007-09-27
```
gksudo gedit /etc/X11/xorg.conf
```

---

