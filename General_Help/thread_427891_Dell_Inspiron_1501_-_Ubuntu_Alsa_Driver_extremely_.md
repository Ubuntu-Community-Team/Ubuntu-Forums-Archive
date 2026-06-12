---
title: "Dell Inspiron 1501 - Ubuntu Alsa Driver extremely quiet audio (video/mp3)"
date: 2007-04-29
forum: General Help
---

### Post by AaronMT on 2007-04-29
This is my pastebin, my Alsa audio is extremely quiet even though volume is at 100% [http://pastebin.ca/465140](http://pastebin.ca/465140)

Device is listed as HDA ATI SB (Alsa Mixer)

Not sure what to do to resolve this. Any help appreciated.

---

### Post by AaronMT on 2007-04-30
bump

---

### Post by dyssident on 2007-12-15
Found a quick fix for quiet audio on the Vostro 1500 that some are having. 

1. Install the alsamixergui package with Synaptic or `sudo apt-get install alsamixergui`
2. Open Applications > Sound and Video > Alsamixergui
3. Jack the PCM levels all the way up. This apparently resets the maximum volume.
4. Close Alsamixergui and turn sound back down to a reasonable level with the hardware buttons or the task bar volume control widget

---

