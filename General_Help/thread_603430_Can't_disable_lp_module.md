---
title: "Can't disable lp module"
date: 2007-11-05
forum: General Help
---

### Post by elsenator on 2007-11-05
Ok, so this is really starting to get on my nerves. I have just installed Xubuntu on a machine and i want to use VMPlayer with it. VMPlayer installed just fine, and it works perfectly except one thing; the parport0 device is in use by the lp module.
Ok, so i decide to disable lp, since i don't need it for anything at all. I add it to the blacklist in /etc/modprobe.d and i disable the cupsys init script(it loads the lp module also).

But, even after doing these two things, the darn lp module still gets loaded! I've been investigating further places that my nemesis gets loaded, but i can't seem to find it.

Can anyone tell me where else the lp module might get loaded even after blacklisting it and disabling the cupsys init script? Any thoughts on this would be greatly appreciated.

---

### Post by elsenator on 2007-11-06
*bump*

---

