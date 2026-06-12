---
title: "how to disable compiz"
date: 2008-04-30
forum: General Help
---

### Post by ubuntu_jazzbach on 2008-04-30
Hi !!!

I just updated to 8.04 and I've noticed that compiz effects are by default enabled, EVEN if I set the value "none" in the Appearance preferences. This causes some of my apps (specially the ones created in "motif") not to work correctly. I use some scientific programs written with Motif and they ran awesome in 7.10 because, if I set the value to "none" in the Appearance preferences, it REALLY meant NONE.

How can I COMPLELETY disable compiz and return to metacity ?

---

### Post by jshbbe on 2008-04-30
Try Alt+F2, then type "metacity --replace" without the quotes.  It works for me.

---

### Post by ubuntu_jazzbach on 2008-04-30
It just turns my monitor off for a second and, nothing changes at all.

---

### Post by ubuntu_jazzbach on 2008-04-30
I've found the way to disable the compositing of metacity:

In a terminal, run:

```

gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool false

```


For further understanding, refer to the following site:

[http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/](http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/)

---

### Post by vishzilla on 2008-04-30
Right click on the menu bar and click on Edit Menu. Under system tools, check Configuration Editor. Now go to Applications>System tools>Configuration Editor. There go to '/desktop/gnome/applications/window_manager'. There change the values of 'current' and default' to '/usr/bin/metacity'
Edit: logoff and login again

---

