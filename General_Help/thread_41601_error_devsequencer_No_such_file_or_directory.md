---
title: "error: dev/sequencer: No such file or directory"
date: 2005-06-14
forum: General Help
---

### Post by abandoned_hussam on 2005-06-14
I just compiled and installed planetpenguin racer on my kubuntu.
I ran it but it gives this error:

open /dev/sequencer: No such file or directory
Fatal signal: Segmentation Fault (SDL Parachute Deployed)

Since I have absolutley no idea what this error mean, I would appreciate any help.
BTW, I never got this error with tuxracer.

---

### Post by skoal on 2005-06-14
type this in a terminal:

sudo modprobe snd-seq

* that should create that device in question.

\\//_

---

### Post by remin8 on 2005-10-20
[quote=skoal]type this in a terminal:

sudo modprobe snd-seq

* that should create that device in question.

\\//_[/quote]


Sweet! That got rid of the same error above for me... now if I can get the sound to actually play!!! Sound on Ubuntu is such a pain!

---

