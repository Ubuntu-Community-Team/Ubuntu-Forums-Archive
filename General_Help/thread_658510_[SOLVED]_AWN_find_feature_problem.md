---
title: "[SOLVED] AWN find feature problem"
date: 2008-01-04
forum: General Help
---

### Post by cartisdm on 2008-01-04
I just installed AWN earlier today and I added the Main Menu Applet.  It works well except I do not have Add/Remove anywhere on the list (also a problem) so I tried searching for it.  I keep getting the following error

"Process /usr/bin/trackerd exited with status 0"

Here's a screen shot

---

### Post by Aathos on 2008-01-04
Which main menu applet are you using?  I have three available: MiMenu, AWN Main Menu, and Cairo Main Menu.  I use MiMenu, which doesn't have Add/Remove... for me either, but the other two do.  I leave a panel with a main menu and systray on it hidden in the bottom corner just to take care of the few things that AWN doesn't do well.  I would suggest creating a launcher in one of the other folders.  The command to use is:
```
/usr/bin/gnome-app-install
```
However, a quick attempt to do that didn't work, even after quiting AWN and restarting it.  I found that it is often necessary to restart AWN to get the menu to update itself.  

The problem with tracker is probably separate, and not related to the lack of Add/Remove... in the menu.

I hope that helps a bit.  Sorry if it is hard to follow.

---

### Post by cartisdm on 2008-01-04
Good call, I completely overlooked those other two Main Menu Apps.  I was using MiMenu but I think I'll start using AWN Main Menu.

However, I liked the Ubuntu orange/red colors of the MiMenu, is there a way to customize the icon for AWN?

---

