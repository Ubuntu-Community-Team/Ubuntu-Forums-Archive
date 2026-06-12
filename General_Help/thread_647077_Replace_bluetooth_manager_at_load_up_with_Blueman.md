---
title: "Replace bluetooth manager at load up with Blueman?"
date: 2007-12-21
forum: General Help
---

### Post by zonky on 2007-12-21
Hi! i've been using Blueman to manage my Nokia N80 / CB2630 connectivity with my ubuntu laptop. Everything is great! - However, it would be nice to not load the default bluetooth manager anymore, as i never use it. (this is the default icon/app loaded when i log in to ubuntu.)

Currently, when i run Blueman, it replaces this icon, and i can then access the functionality through the icon in the top right of gnome (apologies, i don't know what this area is called).

Is there a way to make blueman load at login and/or disable bluetooth manager from starting up?

---

### Post by dcstar on 2007-12-21
> **zonky said:**
> Hi! i've been using Blueman to manage my Nokia N80 / CB2630 connectivity with my ubuntu laptop. Everything is great! - However, it would be nice to not load the default bluetooth manager anymore, as i never use it. (this is the default icon/app loaded when i log in to ubuntu.)

Currently, when i run Blueman, it replaces this icon, and i can then access the functionality through the icon in the top right of gnome (apologies, i don't know what this area is called).

Is there a way to make blueman load at login and/or disable bluetooth manager from starting up?

System-Preferences-Sessions-Startup Programs.

---

### Post by zonky on 2007-12-22
Thanks for that!

For completeness for searchers, i added /usr/bin/blueman to a new startup called blueman, and disabled the bluetooth manager.

If you look in edit -> preferences of blueman, you can set close to notfication area, and also open to notifcation area, so it opens minimised.

---

