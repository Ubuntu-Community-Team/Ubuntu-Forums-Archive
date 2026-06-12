---
title: "xkb in x.org"
date: 2004-11-13
forum: General Help
---

### Post by Razvan on 2004-11-13
Hi People!

thanks for including x.org! :-)

when im logging in via gdm, gnome loads, splashscreen pops up...and there is this error message, i dont know what it tries to tell me since my keyboard runs fine in the selected (german) layout...

```
Fehler beim Aktivieren der XKB-Konfiguration.
Vermutlich liegt ein internes Problem mit dem X-Server vor.

Versionsdaten des X-Servers:
The X.Org Foundation
60801000

Falls Sie einen Fehlerbericht zu diesem Problem einschicken, sollte dieser umfassen:
- Das Ergebnis von xprop -root | grep XKB
- Das Ergebnis von gconftool-2 -R /desktop/gnome/peripherals/keyboard/xkb
```

trying to translate :-)

```
Error while activating XKB-Configuration, probably an internal problem with the x-serer

versoin-data of the x-server:
The X.Org Foundation
60801000

if you send in a problem report please include : 
- otuput of xprop -root | grep XKB
- output of gconftool-2 -R /desktop/gnome/peripherals/keyboard/xkb
```

xprop -root | grep XKB didnt give me any output

gconftool-2 -R /desktop/gnome/peripherals/keyboard/xkb said

```
udssr@Razvan:/etc/X11/xkb $ gconftool-2 -R /desktop/gnome/peripherals/keyboard/xkb
 layouts = [de]
 model = pc105
 overrideSettings = false
 options = []
 update_handlers = []
udssr@Razvan:/etc/X11/xkb $
```

---

