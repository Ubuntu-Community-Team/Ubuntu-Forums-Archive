---
title: "Firefox Flash Instability"
date: 2008-06-24
forum: General Help
---

### Post by The AlGorenator on 2008-06-24
When viewing any flash content in firefox, i was never able to hear sound at any point when i had a music playing program open [eg amarok]. To overcome this i was told to install 'libflash' and it's dependencies. This then causes the problem of instability. Whenever i now view flash content, there's a >50% chance firefox will crash. 

Is there any way i can have both stability and the ability to have my music player working at the same time?

---

### Post by iaculallad on 2008-06-24
Installing the audio support wrapper for non-free flash plugin (libflashsupport) should have solved that problem.

Try installing/using [GNASH ]("http://www.gnu.org/software/gnash/")instead of Adobe's proprietary Flash.

---

### Post by MmmmJoel on 2008-06-24
> **The AlGorenator said:**
> Is there any way i can have both stability and the ability to have my music player working at the same time?

You can try the [Flash 10 beta]("http://labs.adobe.com/downloads/flashplayer10.html"). It supports PulseAudio (giving you audio from multiple sources) and MAY be more stable for you, though it's a crapshoot. Be sure to uninstall Flash 9 (and related packages like libflash) before installing.

---

### Post by The AlGorenator on 2008-06-24
I re-installed all using gnash and it seems to be working with no instability. Many thanks.

---

