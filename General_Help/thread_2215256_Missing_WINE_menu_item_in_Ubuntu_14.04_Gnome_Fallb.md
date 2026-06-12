---
title: "Missing WINE menu item in Ubuntu 14.04 Gnome Fallback"
date: 2014-04-05
forum: General Help
---

### Post by Daniel_Pomietlasz on 2014-04-05
Hello,

I have an issue where the WINE menu is not present in Applications menu under Gnome Fallback in 14.04. 

All the installed WINE applications are showing up under the "Other" Menu Item.

Is this a new behaviour in this version or is something not configured correctly?

I have tried deleting both the ~/.cache and ~/.config directories and also creating a new user and the same behaviour continues.

I also tried replacing gnome-flashback-applications.menu in /etc/xdg/menus with a version from 12.04 and this also did not correct the issue. The wine.menu file is also present in /etc/xdg/menus/applications-merged.

The ony thing I found that worked was to manually edit the gnome-flashback-applications.menu to include a WINE entry but that did not pickup any of the installed applications even on a reinstall.

It seems that all local menu configurations are not used any longer.

Any help on what to look at would be appreciated.

---

### Post by grahammechanical on 2014-04-05
Gnome-session-flashback in 14.04 is not the same as gnome-fallback in 12.04. It may have bugs. You have pointed out something that I did not notice. I have not tried to edit the menu but my guess would be the fact that although Wine is ticked as a menu item to be shown it is not being shown possibly because wine has 2 sub-menu items with each sub-menu having sub-menus inside. It is just a guess but it may be that this 3 tier menu structure of wine is what is stopping the wine menu from showing up under Applications.

I do not use Gnome Flashback. Installing it was just an experiment. But if I was going to mess around with the menu structure I would try to give wine a 2 tier menu structure. May work. May not. If you create a new menu item you will have to populate it with applications. Can this be done by drag and drop? 

Regards.

---

