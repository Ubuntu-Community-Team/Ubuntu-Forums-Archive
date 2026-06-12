---
title: "login screen loads &quot;forever&quot; after a reboot, cant get to my GUI anymore"
date: 2008-06-08
forum: General Help
---

### Post by Cup of Squirrels on 2008-06-08
Hello,

Earlier this evening I noticed that Terminal did not seem to load (The bar would appear in the task bar, but it would eventually close and terminal does not open), so I decided to do a quick reboot.


However, once loaded, the login screen's beige background appeared along with the "loading" cursor... but the login does not appear, and the cursor just keeps on animating. I can ctrl+alt+F1 to the 'console', but that is it. I have tried booting in recovery mode and tried "Fix X server", but to no avail other than my resolution being lowered to 800x600.

The changes I made in the last session were:

-Installed "compizconfig-settings manager" and "simple ccsm" (But with no changes)
-A couple of new themes, one of which is currently in use
-Installed glib
-Installed xmms

What is going on here?


Any help is appreciated

Thanks :)

---

### Post by Titan8990 on 2008-06-09
I would go into recovery mode and uninstall copiz settings manager. I have had three computer that run Ubuntu and only one of those three could actually run compiz.

#apt-get purge compizconfig-settings-manager (or whatever the package is called)

---

### Post by Cup of Squirrels on 2008-06-09
Hi there - I tried what you suggested and cleared out all of the compizconfig installs, but this didn't seem to work.

I will probably uninstall simple ccsm as well and see if that does the trick.

Until then, any other suggestions from anybody? All are greatly appreciated :)

---

