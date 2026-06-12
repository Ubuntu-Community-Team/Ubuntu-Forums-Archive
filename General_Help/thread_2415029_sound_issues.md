---
title: "sound issues"
date: 2019-03-19
forum: General Help
---

### Post by michael_saunders on 2019-03-19
I keep getting an fault with the sound on ubuntu 18.04.2 it goes very staticy with an echo changing from digital stereo to digital surround 5.1 in settings makes it go back to normal but only for a short time it occurs using firefox and rythmbox  sound is through HDMI cable tried other cables and no change a restart seems to stop it for a while but starts up a short time later.

---

### Post by CatKiller on 2019-03-19
It's possible that it's running at the wrong sample rate. That sounds like what you describe.

---

### Post by michael_saunders on 2019-03-20
How would I go about fixing that?

---

### Post by CatKiller on 2019-03-20
There's a file that contains the settings for pulseaudio, including the default sample rate setting. I'm typing from my phone, otherwise I'd find the path for you. The default sample rate, bit rate, and resampling method would be the things to play with, if the problem is that something's causing a mismatch between your source and the device you're playing it back on.

---

