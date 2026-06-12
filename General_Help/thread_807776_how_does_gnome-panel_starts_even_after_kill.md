---
title: "how does gnome-panel starts even after kill?"
date: 2008-05-26
forum: General Help
---

### Post by montamer on 2008-05-26
hi
i have a small doubt,
how does gnome-panel starts again even after issuing 
"kill gnome-panel"
even nautilus too
is there a way to change this behaviour?
and if i want some application to behave like this what should i do?

---

### Post by jeffus_il on 2008-05-26
In the Ubuntu System->Preferences->Sessions Current Session tab, you will see that nautilus and gnome-panel are set-up as "Restart" and it is preferable to leave them that way. If you want to run another session it is better to install it e.g "openbox" and run it from the gdm session menu. and then customize as much as you like. When you run a Gnome Session, the panel and nautilus are an integral part and users require the panel and nautilus (the desktop as well) to restart automatically after a crash. (which hasn't yet happened to me on Hardy).

---

### Post by montamer on 2008-05-29
hi; thanx alot 
sorry for the late reply 
do u know in which file is associated with these configs.

thanx

---

