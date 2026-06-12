---
title: "Ubuntu software center and update manager errors"
date: 2013-05-14
forum: General Help
---

### Post by Nolix on 2013-05-14
Distro version: Ubuntu 13.04
WM - Openbox

When I try to install something through the software center I reiceve this error: ```
Software can't be installed or removed because the authentication service is not available. (org.freedesktop.PolicyKit.Error.Failed: ('system-bus-name', {'name':  ':1.101'}): org.debian.apt.install-or-remove-packages
```

Google searching has given me two options, neither have worked. First was 
```
## GNOME PolicyKit and Keyring
eval $(gnome-keyring-daemon -s --components=pkcs11,secrets,ssh,gpg) &


``` in the autostart.sh file

Second was open your [COLOR=#ffcc66]autostart.sh[/COLOR] file and add [COLOR=#ffcc66]/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1 &[/COLOR] and [COLOR=#ffcc66]eval $(shell gnome-keyring-daemon -s) & [/COLOR]on the last line.

I'm kind of stumped after this :/

---

### Post by Nolix on 2013-05-15
> **Nolix said:**
> Distro version: Ubuntu 13.04
WM - Openbox

When I try to install something through the software center I reiceve this error: ```
Software can't be installed or removed because the authentication service is not available. (org.freedesktop.PolicyKit.Error.Failed: ('system-bus-name', {'name':  ':1.101'}): org.debian.apt.install-or-remove-packages
```

Google searching has given me two options, neither have worked. First was 
```
## GNOME PolicyKit and Keyring
eval $(gnome-keyring-daemon -s --components=pkcs11,secrets,ssh,gpg) &


``` in the autostart.sh file

Second was open your [COLOR=#ffcc66]autostart.sh[/COLOR] file and add [COLOR=#ffcc66]/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1 &[/COLOR] and [COLOR=#ffcc66]eval $(shell gnome-keyring-daemon -s) & [/COLOR]on the last line.

I'm kind of stumped after this :/

Fixed by updating directory for second suggestion.

---

