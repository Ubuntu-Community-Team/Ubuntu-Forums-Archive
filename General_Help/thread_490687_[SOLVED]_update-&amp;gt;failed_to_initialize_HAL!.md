---
title: "[SOLVED] update-&amp;gt;failed to initialize HAL!"
date: 2007-07-02
forum: General Help
---

### Post by T0MA on 2007-07-02
So here is the thing.
I've just installed feisty on my second computer and everything was working fine till i installed some update through the update manager and now I get this error after boot up: Internal error failed to initialize HAL!

Ive searched through the forum for possible solutions bot nothing worked so far. Help!!

---

### Post by osxdude on 2007-07-02
Are you using recovery mode?

---

### Post by T0MA on 2007-07-02
i installed feisty through wubi so im not sure how can i access the recovery mode.. and what should i do once im there?

---

### Post by spnoe on 2007-07-03
Try this in a terminal

sudo /etc/init.d/dbus restart

Found at ([http://ubuntuforums.org/showthread.p...nital](http://ubuntuforums.org/showthread.p...nital) ize+hal)

Good luck 
Steve

---

### Post by spnoe on 2007-07-03
Sorry do not use this it does not work for this problem

Steve

---

### Post by T0MA on 2007-07-03
yeah, well i ended up reinstalling the whole thing and this time NOT installing the update and turning the whole update manager off... doesn't worth it..

---

