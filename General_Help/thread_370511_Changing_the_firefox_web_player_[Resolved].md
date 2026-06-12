---
title: "Changing the firefox web player [Resolved]"
date: 2007-02-25
forum: General Help
---

### Post by laffys on 2007-02-25
How can I change the online internet web player? from totem to mplayer for instance?

---

### Post by aysiu on 2007-02-25
I would close Firefox, press Alt-F2, type ```
gksudo nautilus
``` enter your password, then go to the /usr/lib/firefox/plugins directory and delete anything with the word *totem* in it.

Then start Firefox again.

---

### Post by Azakus on 2007-02-25
Even better, try this:
```
sudo aptitude remove ubuntu-desktop totem-mozilla
#Pick on of these and remove the "#" in front of it
#sudo aptitude install vlc mozilla-plugin-vlc
#sudo aptitude install mplayer mozilla-mplayer
```

---

### Post by laffys on 2007-03-01
Great thanks!!!

---

