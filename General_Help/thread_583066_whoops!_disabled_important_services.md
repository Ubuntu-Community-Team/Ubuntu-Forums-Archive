---
title: "whoops! disabled important services"
date: 2007-10-20
forum: General Help
---

### Post by cheese__monkey on 2007-10-20
I did a stupid thing - I went into System->Administration->Services and turned some of the services off.

When I clicked on one of them the dialog disappeared altogether and then I couldn't get back in - when I try to get to the Services dialog again I get a popup saying "Configuration could not be loaded". Also now when I boot I get a popup saying "Internal error - failed to initialize HAL".

I'm running Feisty if that helps.

I guess these things are controlled by a file somewhere - can anyone tell me which file so I can fix it in console mode and put the services back?

---

### Post by Wilton Matos on 2007-10-29
Please try

  sudo ln -s ../init.d/dbus /etc/rc2.d/S12dbus

When you disable manually ubuntu does not configure dbus, so do this to thing work fine again.

---

