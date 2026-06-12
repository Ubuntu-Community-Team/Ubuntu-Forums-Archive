---
title: "Still having problems with w32codecs"
date: 2006-07-08
forum: General Help
---

### Post by TeeAhr1 on 2006-07-08
Some WMV files give me just audio, others, just video.  Sometimes it plays well for a minute or two and then crashes altogether.  I am using totem, and have installed the latest version of w32codecs as linked to in the wiki.  Anyone got a bead on this?  Thx in advance...

-pete

---

### Post by tsb on 2006-07-08
from terminal type "sudo nautilus"
paste the contents of:  

[http://www1.mplayerhq.hu/MPlayer/releases/codecs/essential-20060611.tar.bz2](http://www1.mplayerhq.hu/MPlayer/releases/codecs/essential-20060611.tar.bz2)

into /usr/lib/win32 after deleting the prior contents of the folder

close the file browser window

if that doesn't work try installing "totem-xine" in synaptic if you haven't already

---

### Post by TeeAhr1 on 2006-07-08
Clarification request: Delete all the files in /usr/lib/win32/, or just the ones that are in the tarball?

EDIT:SOLVED.  Deleted *all* files in the win32 folder, unpacked the tarball into it, and installed totem-xine.  Done, thx!

---

### Post by mlind on 2006-07-08
You can use w32codescs with gstreamer backend too, just install  gstreamer0.10-pitfdll plugin.

---

### Post by quedigg on 2006-07-08
which package are you using ?
also give [easyUbuntu]("http://easyubuntu.freecontrib.org/") a try.

---

### Post by tsb on 2006-07-09
> **mlind said:**
> You can use w32codescs with gstreamer backend too, just install  gstreamer0.10-pitfdll plugin.

Yes, but DVD playback doesn't work with gstreamer, correct?

---

