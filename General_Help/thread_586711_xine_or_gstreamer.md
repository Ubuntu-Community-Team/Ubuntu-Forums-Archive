---
title: "xine or gstreamer?"
date: 2007-10-22
forum: General Help
---

### Post by yjsword on 2007-10-22
Which is better for player multimedia by using totem?
Xine or Gstreamer?

---

### Post by divague on 2007-10-22
i would say totem-xine, because with gstreamer can't see the dvd menus

---

### Post by miggols99 on 2007-10-22
Xine. For some reason GStreamer doesn't work very well for me. I use Kaffeine, which uses Xine, and performs much better than Totem-GStreamer.

---

### Post by yjsword on 2007-10-23
Well,how can i install xine!:KS

---

### Post by ihcnet on 2007-10-23
```
sudo apt-get install xine-ui
```

To just install totem-xine just do ```
sudo apt-get install totem-xine
```

---

### Post by yjsword on 2007-10-23
Must i uninstall gstreamer first before installing xine?

---

### Post by ihcnet on 2007-10-23
Totem-gstreamer will be removed in order to install totem-xine. I think the two packages can't coexist on the same system.

---

### Post by Zzl1xndd on 2007-10-23
> **ihcnet said:**
> Totem-gstreamer will be removed in order to install totem-xine. I think the two packages can't coexist on the same system.

You are correct but the Gstreamer codecs will still be installed and can coexist with the xine ones.

---

### Post by yjsword on 2007-10-23
> **tweakedenigma said:**
> You are correct but the Gstreamer codecs will still be installed and can coexist with the xine ones.
What should i do?
:):)

---

