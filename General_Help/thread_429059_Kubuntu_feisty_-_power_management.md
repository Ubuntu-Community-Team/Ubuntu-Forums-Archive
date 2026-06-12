---
title: "Kubuntu feisty - power management"
date: 2007-04-30
forum: General Help
---

### Post by mykrob on 2007-04-30
Running Kubuntu Feisty on ym desktop..  What is a sure fire way to keep it from turning off my monitor if it sits idle for a few minutes?

If the screensaver is running, it stays on, but if I amwatching TV usung tvtime, or something else that doesnt require a keypress or mouse move, the screen goes black after a time..
-myk

---

### Post by wetland on 2007-04-30
If you go to Menu > System settings > Monitor & Display > Power saving tab > Untick Enable power savings. This suould keep your monitor from shutting off.

---

### Post by mykrob on 2007-04-30
it is already unchecked. I cannot find any more references to power in systemsettings.Am i missing something blatantly obvious?

---

### Post by mykrob on 2007-05-02
bump

---

### Post by strabes on 2007-05-02
Disable your screensaver

---

### Post by mykrob on 2007-05-02
the screensaver is not set to automatically come on.

---

### Post by strabes on 2007-05-02
Don't know then. That's the only option in KDE that I know of.

---

### Post by mykrob on 2007-05-03
anybody else?

Am i the only person having this issue? It is consistent across my two desktops and one laptop.

Thanks,
-myk

---

### Post by MeduZa on 2007-05-06
if you have a nvidia card add this to the xorg.conf:

Section "ServerFlags"
    Option      "blank time" "0"
    Option      "standby time" "0"
    Option      "suspend time" "0"
    Option      "off time" "0"
EndSection

(I don't know if this work on another video card)

---

### Post by mykrob on 2007-05-20
thanks.

Why is this necessary? And why does it seemingly only affect nVidia? My laptop which has INtel graphics doesnt exhibit this behavior.

thanks,
-myk

---

### Post by mithion on 2007-06-24
I've got a similar problem.  But what I want is for my computer's monitor to shutdown.  It's currently set to shutdown after 5 minutes in the power tab.  But after 5 minutes of inactivity, nothing happens.  This is very strange.

Phil

---

