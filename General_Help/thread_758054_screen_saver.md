---
title: "screen saver"
date: 2008-04-17
forum: General Help
---

### Post by hashi856 on 2008-04-17
my monitor keeps going to sleep even though I set the display to never go to sleep.

---

### Post by Brucevdk on 2008-04-17
Are you sure you disabled both the screensaver (System -> Preferences -> Screensavers) and sleeping in power management (System -> Preferences -> Power Management)?

---

### Post by hashi856 on 2008-04-17
> **Brucevdk said:**
> Are you sure you disabled both the screensaver (System -> Preferences -> Screensavers) and sleeping in power management (System -> Preferences -> Power Management)?


yes

---

### Post by Brucevdk on 2008-04-17
Can always try adding these flags to the bottom of your *xorg.conf*:
```

Section "ServerFlags"
   Option "BlankTime" "0"
   Option "StandbyTime" "0"
   Option "SuspendTime" "0"
   Option "OffTime" "0"
EndSection

```

---

### Post by hashi856 on 2008-04-18
> **Brucevdk said:**
> Can always try adding these flags to the bottom of your *xorg.conf*:
```

Section "ServerFlags"
   Option "BlankTime" "0"
   Option "StandbyTime" "0"
   Option "SuspendTime" "0"
   Option "OffTime" "0"
EndSection

```

How do I get to the xorg.conf

---

### Post by Brucevdk on 2008-04-19
> **hashi856 said:**
> How do I get to the xorg.conf

Use *ALT + F2* to get the "Run Application" dialog up and type: *gksudo gedit /etc/X11/xorg.conf* then scroll to the bottom and add those lines above. Make sure you don't touch anything else, or you'll break the configuration file (though it should fallback to the failsafe config if you do manage to break it).

---

