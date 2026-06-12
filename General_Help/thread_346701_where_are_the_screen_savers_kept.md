---
title: "where are the screen savers kept?"
date: 2007-01-26
forum: General Help
---

### Post by slimdog360 on 2007-01-26
I want to hack a couple of the screen savers in Ubuntu but I cant find where they are kept. Ive managed to find a few of them but not all, namely the ones in the/usr/share/applnk/System/ScreenSavers/ directory but they are not the ones which I want to change. The name of the one which I most want to change is GLslideshow. 

So how about it, does anyone know where the screensaver config files are kept?

---

### Post by Ramses de Norre on 2007-01-26
They seem to be in /usr/lib/xscreensaver/, but you'll need to hack the source to change them  I think, no?

---

### Post by slimdog360 on 2007-01-26
thanks. Now I just have to try and find the source code. I have a feelin I know where to get it but sorting though it all I really dont feel like doing. I'll have to think about it. Thanks again.

---

### Post by Ramses de Norre on 2007-01-26
```
apt-get source xscreensaver-gl xscreensaver-gl-extra
```
It'll be in one of these packages.

And it will indeed ask quite some time to read through them and edit the right stuff..

---

