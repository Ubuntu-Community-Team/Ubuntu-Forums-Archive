---
title: "Cannot uninstall this dock app?"
date: 2016-08-19
forum: General Help
---

### Post by KayeNg on 2016-08-19
Hi guys.  Desktop computer is running Lubuntu 16.04.1

I tried to install wbar-config out of curiosity, an app similar to Docky I think.  When I uninstall it and reboot the computer, the dock still appears on the desktop screen, even though Synaptic shows that it has already been removed.   If I execute sudo apt-get remove wbar-config, same thing--it says it is not installed.

Tried it a few times, same result. It cannot be uninstalled, but again, Synaptic shows it is currently NOT in the system.

Suggestions?
Thanks!

---

### Post by mook765 on 2016-08-19
wbar-config is a configuration-tool for wbar and it seems that you successfully removed wbar-config. But this didn't remove wbar itself, wbar is still installed on your system.
if you want to remove wbar from your system you may use the command```
sudo apt purge wbar
```
It might be necessary to reboot the system or logout/login.
The dock should be gone now.
Kind regards...

---

