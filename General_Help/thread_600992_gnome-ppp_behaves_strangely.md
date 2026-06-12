---
title: "gnome-ppp behaves strangely"
date: 2007-11-02
forum: General Help
---

### Post by usien on 2007-11-02
i used gnome-ppp in edgy and fiesty and it worked perfectly.now in gutsy it is able to connect but even though i have enable dock in notification area and minimize when connected, the window stays there after connecting and i cant even minimize it.any help?

---

### Post by yellowbread on 2007-11-03
There is a bug having to do with the interface between gnome-ppp and wvdial. Apparently, wvdial recently changed the format of its output and gnome-ppp is looking for the old format. Not finding it, it hangs at "Athenticating...". Its easy to fix if you don't mind compiling gnome-ppp from source.

[https://bugs.launchpad.net/ubuntu/+source/gnome-ppp/+bug/121487]("https://bugs.launchpad.net/ubuntu/+source/gnome-ppp/+bug/121487")

---

