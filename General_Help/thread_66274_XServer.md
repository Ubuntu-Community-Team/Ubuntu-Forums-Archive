---
title: "XServer"
date: 2005-09-16
forum: General Help
---

### Post by war-totem on 2005-09-16
the problem started when i tried to logout of fluxbox to load up gnome.  however my pc rebooted instead and gave me a can not start X Server.  now i get the error: couldnt connect to XServer.

completely dumbfounded and worried.

anyone?

---

### Post by arnieboy on 2005-09-16
[QUOTE=war-totem]the problem started when i tried to logout of fluxbox to load up gnome.  however my pc rebooted instead and gave me a can not start X Server.  now i get the error: couldnt connect to XServer.

completely dumbfounded and worried.

anyone?[/QUOTE]
what does $HOME/.xsession-errors tell u?
try doing a ```
sudo dpkg-reconfigure xserver-xorg
```

---

