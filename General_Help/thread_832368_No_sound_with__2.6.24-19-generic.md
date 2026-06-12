---
title: "No sound with  2.6.24-19-generic"
date: 2008-06-17
forum: General Help
---

### Post by _sAm_ on 2008-06-17
I updated to 2.6.24-19-generic with the update manager and now I have no sound at all(my soundcard worked with 2.6.24-16 to 18, both generic and server).

The volum icon is telling me;
*No volume control GStreamer plugins and/or devices found.*

Any advice?

---

### Post by Zorael on 2008-06-17
Make sure you have the **linux-generic** package installed. You may be missing linux-ubuntu-modules-2.6.24-19-generic which linux-generic pulls as a dependency. You can find and install the linux-generic package in Synaptic, Adept Manager, or through terminal commands.
```
$ sudo aptitude install linux-generic
```

---

### Post by _sAm_ on 2008-06-17
Thank you - that did the trick - sound is back :)

---

