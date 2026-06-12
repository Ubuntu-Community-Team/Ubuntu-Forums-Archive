---
title: "No audio with Fluxbox"
date: 2008-06-12
forum: General Help
---

### Post by mishathegoat on 2008-06-12
Hey everyone!

I recently install fluxbox on my Ubuntu Server 8.04 machine. With that, I also installed alsa, alsa-utils, SoX and I still can't get my audio to work! Any ideas?

---

### Post by mishathegoat on 2008-06-12
Found out how to fix the problem. By default all the channels are muted after you install ALSA.
I needed to open the terminal and run:

```
alsamixer
```

Then I needed to unmute and raise the volume on everything. To unmute I pressed the "m" key on my keyboard whenever I navigated to a volume control with "MM" below it (Which would then change it to 00). To turn up the volume I pressed the "UP" key over each volume control.

---

### Post by takuruu on 2009-06-27
Oh thx for your experience!!

---

