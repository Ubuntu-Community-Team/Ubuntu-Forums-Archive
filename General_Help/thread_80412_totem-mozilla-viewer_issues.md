---
title: "totem-mozilla-viewer issues"
date: 2005-10-22
forum: General Help
---

### Post by `GooZ´ on 2005-10-22
When I try to open a stream in FF, it loads the totem-mozilla-viewer. W32 codecs are installed properly, but still it will only load 3 secs of the stream, and then it stops. So I was willing to uninstall it and try the other totem stream plug (don't remeber it's name, but it's installed), but I can't uninstall totem-mozilla-viewer, 'cause I can't find it anywhere in Synaptic... What should I do?

---

### Post by zafar on 2005-10-22
The only other well working mozilla plugin I know of that works is mplayerplug-in (mozilla-mplayer). To get totem-mozilla to be disabled, and install that plugin, simply do the following:

Open up a terminal and input:
```
cd /usr/lib/mozilla-firefox/
sudo mkdir totem
cd plugins
sudo mv libtotem* ../totem
```
(these steps move the totem mozilla plugin out of the plugins folder so that they will not be detected and enabled, to use them again move them back into the plugins folder)

Then open up synaptic and install:
mplayer-586 for a version with a gui OR mplayer-nogui
and also install mozilla-mplayer

These steps should fix streaming video

---

### Post by `GooZ´ on 2005-10-22
Works like a charm! Thanks ALOT!

---

