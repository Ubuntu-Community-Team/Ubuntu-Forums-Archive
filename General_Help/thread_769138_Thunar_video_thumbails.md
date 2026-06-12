---
title: "Thunar video thumbails"
date: 2008-04-26
forum: General Help
---

### Post by belovedmonster on 2008-04-26
With Xubuntu 7.10 I added video codecs using Automatix and after this I had no problems with Thunar generating thumbnails for my videos. But after installing Xubuntu 8.04 and adding the codecs via the prompt in Totem I find I can play the videos fine but I'm not getting any thumbails in Thunar.

What do I need to do to get them?

---

### Post by jdarias on 2008-05-05
hello! Got this issue too.
```
sudo apt-get install ffmpegthumbnailer thunar-thumbnailers
```
However, video thumbnails will look uselessly small. This seems to be a constraint of design in thunar. Zooming in makes all icons and thumbnails bigger. 
[http://bugzilla.xfce.org/show_bug.cgi?id=1596](http://bugzilla.xfce.org/show_bug.cgi?id=1596)
HTH

---

