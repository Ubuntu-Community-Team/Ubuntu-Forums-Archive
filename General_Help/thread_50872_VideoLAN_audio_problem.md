---
title: "VideoLAN audio problem"
date: 2005-07-21
forum: General Help
---

### Post by eelozano on 2005-07-21
When I open up VLC and play a video I get this error.

[00000270] oss audio output error: cannot open audio device (/dev/dsp)

Any thoughts?

P.S. I open it from the command line and thats the error it spits out.

---

### Post by NeoChaosX on 2005-07-21
sudo apt-get install vlc-plugin-alsa

---

### Post by eelozano on 2005-07-21
I still get the exact same error.

Thanks for the reply though.

Any other thoughts?

---

### Post by eelozano on 2005-07-21
I've gotten the sound to work (installed two other audio packages).

It still spits out these errors.

[00000274] oss audio output error: cannot open audio device (/dev/dsp)
[00000274] arts audio output error: arts_init failed (loading the aRts backend "/usr/lib/libartscbackend.la" failed)


Should I just ignore them?  Or is there a reason I should look deeper into this problem.

---

