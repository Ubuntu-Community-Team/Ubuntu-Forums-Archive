---
title: "Amarok startup"
date: 2006-12-17
forum: General Help
---

### Post by seelk on 2006-12-17
Is it me or is the Amarok startup time very slow in Ubuntu (Gnome)?  It's so slow that I sometimes think the app is not starting so I click on the shortcut again to fire it up.

---

### Post by raul_ on 2006-12-17
Sometimes it's hidden in the notification area (system tray as some call it) . Have u tried Listen music player? It has the same features (plus an option that tells u similar artists to the one you are listening to) and it's designed for Gnome

---

### Post by seelk on 2006-12-18
> **raul_ said:**
> Sometimes it's hidden in the notification area (system tray as some call it) . Have u tried Listen music player? It has the same features (plus an option that tells u similar artists to the one you are listening to) and it's designed for Gnome

It is not hidden in the notification area.  It's a clean start each time.  I also haven't tried Listen music player.  Any other ideas?  I don't think I'm ready to give up on this issue because it was not the case in Dapper.

---

### Post by NeoChaosX on 2006-12-18
The start-up is slow because the system is loading the KDE libraries that Amarok needs. If you wanted something that starts up faster, I'd recommend using a GTK/GNOME-based music player.

---

### Post by seelk on 2006-12-18
> **NeoChaosX said:**
> The start-up is slow because the system is loading the KDE libraries that Amarok needs. If you wanted something that starts up faster, I'd recommend using a GTK/GNOME-based music player.

Is there a way to have the libraries load ahead of time (maybe during boot)?

---

### Post by FaceorKneecaps on 2006-12-18
Oki....I am a first degree noobie here (seconds day with Ubuntu only), but I managed to get Amarok to load smoothly on both "quick" and Full reboot. I added KLauncher and kdeinit  in System- Preferences-Sessions-Startup.  It worked here on 6.10, but I have no idea why. :-k 
It didnt work for Ktorrent though but I just use freeloader instead.

Someone know what I did?

---

