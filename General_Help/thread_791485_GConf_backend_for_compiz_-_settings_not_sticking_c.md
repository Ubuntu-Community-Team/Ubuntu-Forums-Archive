---
title: "GConf backend for compiz - settings not sticking correctly"
date: 2008-05-12
forum: General Help
---

### Post by Psyker7 on 2008-05-12
So when I set the backend to gconf for ccsm, and try to change a few settings they don't seem to stick properly. Not only that but they change to something I didn't set.

Default settings for 3 things:
General Settings -> Window Menu -> <Alt>Button 3
Move Window -> Initiate Window Move -> <Alt>Button 1
Resize Window -> Bindings -> Initiate Window Resize (mouse) -> <Alt>Button 2

I was attempting to remove the window menu binding, and change the resize window setting to <alt>Button 3

Yet upon changing ANY of these settings, as soon as I clicked back to go to the main ccsm window, it seemed to change Move Window to Button 1 - ie without Alt.... very strange.

If I change the backend to flatfile, then I can change these settings just fine.

I did have a small error in my gconf I discovered with an empty setting set to [] instead of empty... but even after fixing that I still have this issue.

ANyone else? or should I file this as a bug report?

---

### Post by Zorael on 2008-05-12
It's a widely known issue, and the workaround - as you said - is to use flatfile instead.

---

### Post by Psyker7 on 2008-05-12
Strange how googling turned up a blank then :|

Thanks!

---

