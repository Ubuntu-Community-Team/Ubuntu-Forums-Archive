---
title: "Can I reset the desktop?"
date: 2004-11-08
forum: General Help
---

### Post by Mike Finn on 2004-11-08
Fiddling is a hazard!!! :)

I rearranged my desktop panels and when I had everything how I like it I deleted the top panel..... NOW I realize that I didn't put the computer menu anywhere :( The one with Synaptic, add users, printer setup etc..... 

So I would like to set everything back to how it was originally installed and try again.... any ideas??

I guess just adding those features would be ok too.... BUT where are they located??

Mike

---

### Post by tfwo on 2004-11-08
Yes, you can right-click on the panel -> "Add to panel..." then select Menu Bar (not GNOME Main Menu, it has the foot icon as well). If you want to purge all configuration to the defaults, then logout, switch to console (CTRL-ALT-F1), login an run:
$ gconftool-2 --shutdown
$ rm -rf .gnome*
$ rm -rf .gconf
logout, and switch back with CTRL-ALT-F7

---

### Post by adbak on 2004-11-08
On your existing panel, right click then left click New Panel.  Move the panel to where you want it, then right click, then left click Add to Panel and add anything you want.

---

### Post by Mike Finn on 2004-11-08
Thank you.... Easy uh!!

Mike

---

