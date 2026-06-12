---
title: "No headphone sound in Ubuntu 13.04 Asus U57A"
date: 2013-09-29
forum: General Help
---

### Post by BlackL1ght on 2013-09-29
When I plug in my headphones, the speakers stop, but nothing plays in the headphones. It's not just muted either. I've looked at alsamixer, but my headphones aren't muted either.

Any ideas?

---

### Post by Yellow Pasque on 2013-09-30
More info please: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by BlackL1ght on 2013-10-03
It fixed itself for about a day and then stopped working again. Here's the info: [http://www.alsa-project.org/db/?f=7bc982cccfe84db354bea92445a1591025e39f09](http://www.alsa-project.org/db/?f=7bc982cccfe84db354bea92445a1591025e39f09)

Also, now I am missing the sound icon in the top bar.

---

### Post by Yellow Pasque on 2013-10-03
Try resetting the pulseaudio config:
```
rm -r ~/.config/pulse; pulseaudio -k
```

---

### Post by BlackL1ght on 2013-10-04
Hey that worked! (mostly). I have sound from my headphones again. How can I get the volume icon back in the title bar?

---

### Post by Yellow Pasque on 2013-10-04
> How can I get the volume icon back in the title bar?
Have you logged out yet?

---

### Post by BlackL1ght on 2013-10-04
Just relogged. No change.

---

### Post by Yellow Pasque on 2013-10-04
Well then, I'm not sure (I don't personally use Unity desktop or know much about it).

---

