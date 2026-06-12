---
title: "Compiz broken after playing with ATI drivers"
date: 2008-05-08
forum: General Help
---

### Post by PopeMatt on 2008-05-08
Okay, so here's what happened. I was living in a happy little Gutsy world, when the tempting spectre of Hardy came into my life. Hardy destroyed my computer in a number of new and exciting ways. Anyway, I downgraded to Gutsy (yay for separate home partitions).

Everything, including compiz, was working well, except that when playing video and then moving the desktop cube, the video didn't move with the cube. Not a huge problem, but it worked perfectly before the upgrade.
So I enabled the restricted ATI drivers, which I remember doing before.
That broke compiz. After using the restricted drivers, I got a No Composite extension error.
So I disabled the ATI driver, but compiz still didn't work. I was getting a "Desktop Effects cannot be enabled error."

I tried installing ATI drivers with Envy, to no avail. I uninstalled those, and now I believe I am using the standard Ubuntu video drivers, but I can't use compiz.

This is the output of compiz, run from terminal:
matt@Realize:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"


Please help. I love my compiz functionality.

--Matt

---

### Post by macaholic on 2008-05-08
Hey, my name is Matt Too! Anyway, you could look [here]("http://combatwombat.7doves.com/2007/10/31/gutsy_effort_in_new_ati_driver"), just the xorg section, it may help you with your predicament with evil ATI drivers and compiz.

---

### Post by PopeMatt on 2008-05-08
sudo apt-get install xserver-xgl


...That was all I had to do.
Stupid world.


Thanks a lot, Matt.

:-)

---

