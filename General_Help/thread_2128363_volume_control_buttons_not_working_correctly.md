---
title: "volume control buttons not working correctly"
date: 2013-03-22
forum: General Help
---

### Post by opfeld on 2013-03-22
When I push my volume keys it brings up the volume on screen and changes it, but it doesn't affect the sound.  If I click on the panel sound applet and manually move that, it does change the sound.  Anyone else run into this?

---

### Post by dino99 on 2013-03-23
it could be either a kernel issue or a pulseaudio one about the sound chipset detection. Is it a HDA one ?

report against pulseaudio: ```
 ubuntu-bug pulseaudio 
```

---

