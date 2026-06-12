---
title: "Command line to restore/minimize/maximize window?"
date: 2006-07-26
forum: General Help
---

### Post by genyue on 2006-07-26
For example, I want to restore the Krusader (file manager application) by 'typing', what's the command for it? Or rather, is it possible, is there such a feature?

Please do include the command for maximizing and minimizing windows, if it's possible to be done.

If there's some external program with such a feature, please do let me know as well.

---

### Post by jayemef on 2006-07-26
Alt+tab will just about always do it. Otherwise it depends on the window manager you're using.

---

### Post by genyue on 2006-07-26
But imagine if I got like 30 windows running at the same time, in foreground? 

It would take a little time to find that window, ya?

---

### Post by jayemef on 2006-07-27
Only if you haven't brought that window to focus since doing so with other windows. Alt+tab can be compared to a cache -- anything you've used recently will be at the beginning of the list. Other stuff drops down.

In any case, you wouldn't have that many items open on one workspace anyway. Even if you did, it would take just as long to find the item in your taskbar. Plus, I'm fairly certain the restore shortcut only works on the window you just minimized.

---

### Post by PhilipGanchev on 2007-03-19
Now you can use the Deskbar panel applet to switch between windows by typing their names.  You need to install the applet first using
  sudo apt-get install deskbar-applet

---

### Post by newsun on 2007-11-13
wmctrl will do what you want and it is in the repos

[http://www.oreillynet.com/sysadmin/blog/2004/12/wmctrl_shade_move_resize_windo.html](http://www.oreillynet.com/sysadmin/blog/2004/12/wmctrl_shade_move_resize_windo.html)

[http://www.sweb.cz/tripie/utils/wmctrl/](http://www.sweb.cz/tripie/utils/wmctrl/)

---

