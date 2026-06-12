---
title: "Gnome desktop corrupted"
date: 2006-11-26
forum: General Help
---

### Post by FrankVdb on 2006-11-26
Because of the many troubles I had with Edgy, I returned to Dapper, only to have my Gnome desktop broken...

When logging in, Dapper tries to load the Gnome desktop but hangs when loading the panels and then goes back to the login screen. It requires me to log in some ten times, then suddenly I get in.

The only thing I did was adding a panel with icons to the right side of the screen. Now it is showing up to the left of the screen.

Also, I did an Xserver reconfigure but that didn't solve the Gnome problem. In addition, a couple of keys on my keyboard are no longer working.

Any ideas on how to restore my desktop? Thanks in advance.

---

### Post by AlphaMack on 2006-11-26
Have you tried logging into GNOME safe mode?  And perhaps removing saved sessions?

---

### Post by FrankVdb on 2006-11-26
I tried all modes but the problem remains.

---

### Post by xopher on 2006-11-26
> And perhaps removing saved sessions?

^ That would probably fix it if you have gnome properly installed.

---

### Post by FrankVdb on 2006-11-26
Hm, how do I remove previous sessions? How many sessions does Gnome store?

---

### Post by FrankVdb on 2006-11-26
The last two times I managed to log in after numerous attempts, I get an error message mentioning the XKB configuration. I'm using the Dutch interface, it is saying something like "error activating XKB configuration". "This may happen when:
- the libxkeyboard library is faulty
- an error in the X server has occurred (xkbcomp, xmodmap auxiliary programmes)
- X server has an incompatible libxkbfile implementation

X server version:
the X.Org Foundation
70000000"

Also, it says that I need to report the outcome of 'xprop -root | grep XKB' if I want to file an error report, however I can't input the | sign since my keyboard is broken (I can't use the Alt Gr key).

Does anyone know how I can correct this? Thanks...

---

### Post by FrankVdb on 2006-11-27
Fed up with it, I'm going back to Windows 2000 on my laptop.

---

