---
title: "No video in totem"
date: 2004-10-15
forum: General Help
---

### Post by spaaz9 on 2004-10-15
I have sound, but no video in totem.  I've tried reinstalling it, but no joy.  I have a nVidia Riva TNT2 32MB PCI card.  Any ideas?

---

### Post by im_ka on 2004-10-15
gstreamer/totem doesnt support many video formats. add this line to /etc/apt/sources.list :

```
deb ftp&#58;//ftp.nerim.net/debian-marillat/ unstable main
```

and then install mplayer which should play most (if not all) video formats.

```
sudo apt-get install mplayer
```

---

