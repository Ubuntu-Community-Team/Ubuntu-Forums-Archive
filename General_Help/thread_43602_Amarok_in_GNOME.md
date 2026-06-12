---
title: "Amarok in GNOME?"
date: 2005-06-22
forum: General Help
---

### Post by Prudentissimus on 2005-06-22
will it work in GNOME?

---

### Post by xalphas on 2005-06-22
Sure..just select amarok with apt-get and install it with kde dependencies. You don't need all of kde but only required ones.

---

### Post by angkor on 2005-06-22
Amarok will need an engine so you will need to install some enginesl:

```
 apt-cache search amarok-engine
amarok - versatile and easy to use audio player for KDE
amarok-arts - aRts engine for the amaroK audio player
amarok-engines - output engines for the amaroK audio player
amarok-gstreamer - GStreamer engine for the amaroK audio player
amarok-xine - xine engine for the amaroK audio player
``` 

and try em out to see which works (best).

---

