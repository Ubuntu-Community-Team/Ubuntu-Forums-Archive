---
title: "Only ctrl + mouse click works after installing Gnome desktop &amp; reverting to Unity"
date: 2016-08-03
forum: General Help
---

### Post by foxheppa on 2016-08-03
I have Ubuntu 14.04. Installed gnome-desktop & shell through Ubuntu Software center. Did not like it and reverted back to Unity, now mouse is acting weirdly. CTRL + click acts like a normal mouse click, normal click does nothing. :(

Tried reinstalling unity and doing update & upgrade, no help.

---

### Post by foxheppa on 2016-08-03
Ok, solved! At some point took away the ALT modifier in gnome-tweak-tool. Somehow reverting back to Unity mangled then the mouse functions so that it was impossible to click anything without pressing CTRL + click. This solved the issue: [http://askubuntu.com/questions/760654/cick-to-focus-is-not-working-16-04](http://askubuntu.com/questions/760654/cick-to-focus-is-not-working-16-04)

> [COLOR=#111111][FONT=Ubuntu]Open dconf-editor and navigate to [/FONT][/COLOR]org.gnome.desktop.wm.preferences[COLOR=#111111][FONT=Ubuntu] and make sure [/FONT][/COLOR]mouse-modifier-button[COLOR=#111111][FONT=Ubuntu] and [/FONT][/COLOR]raise-on-click[COLOR=#111111][FONT=Ubuntu] are both set to default. If that doesn't do it, maybe another setting in there is not default and causing your issue.[/FONT][/COLOR]

---

