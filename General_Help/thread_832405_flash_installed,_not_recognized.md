---
title: "flash installed, not recognized"
date: 2008-06-17
forum: General Help
---

### Post by ac3raven on 2008-06-17
I've installed the flash plugin for firefox, but firefox doesn't seem to be recognizing it.  And when I try install it again it says its already installed.  help maybe

---

### Post by Zorael on 2008-06-17
32-bit or 64-bit?


For 32-bit:
```
$ sudo update-alternatives --config mozilla-flashplugin
```
Pick **/usr/lib/flashplugin-nonfree/libflashplayer.so**.

---

### Post by ac3raven on 2008-06-18
32 bit, it's eeexubuntu on my EeePC.

---

### Post by avtolle on 2008-06-18
Be sure that gnash and the gnash plug-in are removed. Check in Synaptic, and if they are installed (as seems likely), mark for complete removal, then click on Apply.

---

