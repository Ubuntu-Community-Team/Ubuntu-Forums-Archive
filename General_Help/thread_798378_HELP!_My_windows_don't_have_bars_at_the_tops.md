---
title: "HELP! My windows don't have bars at the tops"
date: 2008-05-18
forum: General Help
---

### Post by BenLi on 2008-05-18
All my windows lack the bar at the top of the window with the close, minimize, and maximize options. This also means I cannot drag.

I'm running on a clean install of 7.10 with a X1400 with fglrx drivers.

---

### Post by TeoBigusGeekus on 2008-05-18
Try to disable compiz...

---

### Post by angry_johnnie on 2008-05-18
go to system > preferences > advanced desktop effects

(or hit alt + f2 and type **ccsm**)

And see if the **Window Decorations** plugin is enabled.

If it is, and you still don't have decorations, click on the window decorations button.

Go down to where it says **command**.

By default, it's set to [B]/usr/bin/compiz-decorator
[/B]
You could try **/usr/bin/gtk-window-decorator --replace**

or maybe **/usr/bin/emerald --replace** (if you have installed emerald).

An easier way to do this would be to install fusion-icon.

```
sudo apt-get install fusion-icon
```

Then you can launch it by either going to Applications > System Tools > fusion icon

or by hitting Alt + F2 and then typing **fusion-icon**.

You'll then see it on the system tray.

Right-click on it, and find the Window Decorations option, where you'll be able to choose between emerald (if you have it), or gtk.

---

