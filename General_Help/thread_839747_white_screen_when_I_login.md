---
title: "white screen when I login"
date: 2008-06-24
forum: General Help
---

### Post by xigen on 2008-06-24
This morning I added some updates.  When I re-booted my system the screen came up completely white (no wall paper/menu).  I tried hitting all combinations of alt+F(1-12), and ctrl+F(1-12) and nothing happened.

When I hit ctrl+alt+BackSpace I see my normal background and toolbars as X shuts down. 

How do I get my screen back?

System: 
Hardy-64
ATI-Radeon Graphics

---

### Post by spiderbatdad on 2008-06-24
do you get a login screen? If so choose failsafe gnome then open  a terminal and run ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Otherwise, try booting into recovery mode then run: su your_username then the above command without sudo.

Hope that helps...not sure.

---

### Post by xigen on 2008-06-29
Well - this is turning out to be a pickle.

I tried 
sudo dpkg-reconfigure -phigh xserver-xorg
I got a warning from the system.

I uninstalled all awn files 
[http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml](http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml)
* it is toward the bottom

I tried uninstalling/re-installing Gonme

I tried to reset Gnome defaults
 rm -rf .gnome .gnome2 .gconf .gconfd .metacity

I still get a big white screen with an active cursor when I log in.

...

What approach would you suggest I try next?

---

