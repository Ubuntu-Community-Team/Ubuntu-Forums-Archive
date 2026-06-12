---
title: "Getting multiple key events from lirc for xvmc"
date: 2014-10-10
forum: General Help
---

### Post by rich-midwinter on 2014-10-10
I'm using an Apple TV remote to control XBMC on a Mac Mini. This used to work, I haven't used the machine for a while and dist-upgraded it yesterday.

Now I'm seeing when I press Up/Down the menu navigation goes up and down but a volume up/down GUI appears too. Also, if I press play/pause to enter into a folder in a menu it actions it twice - the first item in the list is .. so it navigates straight back. I see two codes received for a single keypress in irw (which I'm guessing is key).

Left/right seem to work fine. Any ideas how I can fix this? Thanks in advance.

---

### Post by rich-midwinter on 2014-10-10
Ok. I've found a repeat 0 option for lirc which seems to prevent multiple events. Only issue is now for the up/down I'm only getting the volume controls. Think these might be being intercepted by XFCE, so if I can disable XFCE's lirc integration it might just work. Actually, I think this happens when run from Openbox too but it must be something like that. Maybe they both use some Gnome volume service.

---

### Post by rich-midwinter on 2014-10-10
Changed my mind a bit again. XBMC must be controlling the volume tool as the look and feel changes when I change the skin.

---

### Post by rich-midwinter on 2014-10-11
**** this!

---

