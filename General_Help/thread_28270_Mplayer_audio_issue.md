---
title: "Mplayer audio issue"
date: 2005-04-19
forum: General Help
---

### Post by eXidos on 2005-04-19
I have installe all the codecs for audio and video, i installed mplayer but when i go through console to launch a video it says:

audio_setup: Can't open audio device /dev/dsp: Device or resource busy alsa-init: 1 soundcard found, using: default

I have no other audio programs running that would effect it.

any suggestions?

---

### Post by speedman on 2005-04-19
Edit /etc/mplayer/mplayer.conf and

change: ao=alsa,

to: ao=esd,


Regards,

SM

---

