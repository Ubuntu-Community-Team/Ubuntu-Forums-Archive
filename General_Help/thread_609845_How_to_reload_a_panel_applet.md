---
title: "How to reload a panel applet?"
date: 2007-11-11
forum: General Help
---

### Post by Goombie on 2007-11-11
I recently added a new applet to my Gnome-Panel (menu-file-browser-applet), which I have to change the settings for through gconf; the applet's author hasn't coded a preference dialog yet. :( After I change the applet's settings, I have to log off and back on to see the results. 
My question is, is there any way to just reload the applet itself without having to log off and back on? Thanks!

:popcorn:

---

### Post by eggdeng on 2007-11-11
You can restart the panel with ```
killall gnome-panel
```

---

