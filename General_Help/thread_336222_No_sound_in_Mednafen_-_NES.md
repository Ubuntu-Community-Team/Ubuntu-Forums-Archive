---
title: "No sound in Mednafen - NES"
date: 2007-01-11
forum: General Help
---

### Post by straxus on 2007-01-11
I installed Mednafen 0.7.1 from the following package which was built for Edgy (which I'm using):

 [http://www.zshare.net/download/mednafen_0-7-1-1_i386-deb.html](http://www.zshare.net/download/mednafen_0-7-1-1_i386-deb.html)

Gameboy games have sound.  When I load up a NES game, I get the following error:

 Initializing sound...
  Using "ALSA" audio driver with device "default":ALSA Error: snd_pcm_hw_params_set_channels(alsa_pcm, hw_params, format->channels) Invalid argument
Error opening a sound device.

Sound works in 0.6.2 from repos.  Any ideas?

---

### Post by Mednafen on 2007-01-16
Use "-sounddriver oss" as a quick fix.

---

