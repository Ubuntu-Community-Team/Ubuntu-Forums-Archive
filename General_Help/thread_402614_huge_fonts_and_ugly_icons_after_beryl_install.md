---
title: "huge fonts and ugly icons after beryl install"
date: 2007-04-06
forum: General Help
---

### Post by cptjaben on 2007-04-06
I just installed Beryl follow [this guide]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI#Automatic_installation"). Everything works fine, but all my fonts are quite large, also my icons are quite old and ugly looking and the shutdown button and restart button are missing. does anyone know how to fix these problems?

---

### Post by cisforcojo on 2007-04-06
It could be XGL that's throwing you off. 
Try running: 

$ gnome-settings-daemon

in a terminal and see if that helps! 

If this solves your problem, just go to System->Preferences->Sessions and add it to your Startup Programs.

---

### Post by cptjaben on 2007-04-06
Awesome, that worked perfectly. Thanks

---

### Post by strabes on 2007-04-07
You could add this to startup programs in gnome-session-properties.

---

