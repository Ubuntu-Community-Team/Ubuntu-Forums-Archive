---
title: "RealPlayer won't open"
date: 2005-03-30
forum: General Help
---

### Post by NeoChaosX on 2005-03-30
I just installed RealPlayer, but the program just won't open. If I open the menu entry or type "realplay" in the console, nothing comes up. No error messages seem to come up in the console either.  When I installed it, I installed the program to /opt/RealPlayer and set the symbolic links prefix to /usr. Is there anyway to fix this?

---

### Post by turnip_flan on 2005-03-30
Hello,

I had the same problem - try unchecking both the boxes under the general tab in the sound preferences box under the preferences menu. This allowed my RealPlayer to run and everything works fine now.

Question for others - what have I now turned off?

Turnip

---

### Post by NeoChaosX on 2005-03-30
It disables the ESD sound server. In turn, you have to use ALSA as your main sound system. At this point, I don't want to have to enable ALSA mixing again (I had mixed results with it enabled), so I'm not sure about this. If only there was a way to force Real to use ESD...  :cry:

EDIT: Anybody know of any alternate players that can play Real media with the right codecs? Or is the Real player the only way?

---

