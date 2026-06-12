---
title: "after upgrade from 18.04 to 20.04 no sound in chromium"
date: 2020-10-06
forum: General Help
---

### Post by anewbie on 2020-10-06
After  i upgraded from 18.04 to 20.04 i no longer have sound from videos played in chromium-browser. Sounds works fine with vlc, firefox, ....

I ran pavucontrol and i can see (for example) firefox when it runs but chromium doesn't show up. I know what 20.04 they are sandboxing chromium but i'm unsure how to fix the audio issue with this sandbox.

---

### Post by ActionParsnip on 2020-10-06
[https://askubuntu.com/questions/1086658/no-sound-audio-in-chrome-ubuntu-18-04lts](https://askubuntu.com/questions/1086658/no-sound-audio-in-chrome-ubuntu-18-04lts)

Does this help?

---

### Post by anewbie on 2020-10-06
It helps for the logged in user - specifically adding the line:

load-module module-stream-restore restore_device=false
--
However alternative user ids still have no sound but firefox works fine so the problem isn't totally fixed.

> **ActionParsnip said:**
> [https://askubuntu.com/questions/1086658/no-sound-audio-in-chrome-ubuntu-18-04lts](https://askubuntu.com/questions/1086658/no-sound-audio-in-chrome-ubuntu-18-04lts)

Does this help?

---

### Post by anewbie on 2020-10-06
Actually here is the error I think but not sure - chrome from the other user can't access /usr/share/alsa/alsa.conf - the user can access thta file just not chrome.

```
ALSA lib conf.c:3916:(snd_config_update_r) Cannot access file /usr/share/alsa/alsa.conf
ALSA lib pcm.c:2495:(snd_pcm_open_noupdate) Unknown PCM default
[16836:16836:1006/171553.450433:ERROR:alsa_util.cc(204)] PcmOpen: default,No such file or directory
ALSA lib conf.c:3916:(snd_config_update_r) Cannot access file /usr/share/alsa/alsa.conf
ALSA lib pcm.c:2495:(snd_pcm_open_noupdate) Unknown PCM plug:default
[16836:16836:1006/171553.450633:ERROR:alsa_util.cc(204)] PcmOpen: plug:default,No such file or directory
```

---

### Post by anewbie on 2020-10-09
Any suggestions on how to fix this under 20.04 - is there a way to get a non-snap version of chromium ?

---

