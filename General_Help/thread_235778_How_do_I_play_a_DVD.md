---
title: "How do I play a DVD?"
date: 2006-08-13
forum: General Help
---

### Post by sean_ on 2006-08-13
Hey guys, I searched on the Ubuntu Guide, and some of google and couldn't find this. I'm trying to play a DVD (A legal one, aka, on a CD) and I tried to MPLayer video and I can't find out how to open a DVD. Is there a special program I can grab that can read my CD and play the DVD?

---

### Post by vijirajan on 2006-08-13
Try, **totem**. Its under Applications->Sound and Video->Movie Player menu item.

---

### Post by sean_ on 2006-08-13
Okay, Totem says I don't have the right plugin for it

---

### Post by Dgurion on 2006-08-13
You can follow the instructions in the Ubuntu Wiki:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

You need to enable the extra repositories, which is outlined in the wiki.. (I think)

---

### Post by vijirajan on 2006-08-13
You could install totem-xine too. 

```

sudo apt-get install totem-xine

```

NOTE: This will uninstall gstreamer based totem.

---

### Post by nix4me on 2006-08-13
Use totem-xine or mplayer with w32codecs.  And follow the restricted formates link that was posted previously.

nix4me

---

### Post by njzillest on 2006-08-14
to get the codecs, i suggest using the BEST autoscripter- Automatix. 
It will work for most of the videos you play, including AVI, MPEG, and DVD (i think vorbis)

hope this helped

---

