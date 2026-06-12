---
title: "totem-xine and totem-gstreamer problems"
date: 2005-05-08
forum: General Help
---

### Post by itatabitovski on 2005-05-08
This is the situation,

When i have installed totem-gstreamer i am getting both video and sound but the video is choppy and desynced == unwatchable

When i install totem-xine, the video is just perfect but i dont have sound at all!

I have installed both w32codecs and the codecs from mplayer.


any ideas ?!?

```
 lsmod | grep snd
snd_intel8x0           32352  2
snd_ac97_codec         74144  1 snd_intel8x0
snd_pcm_oss            52132  1
snd_mixer_oss          19680  2 snd_pcm_oss
snd_pcm                94696  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25060  1 snd_pcm
snd                    55012  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixe r_oss,snd_pcm,snd_timer
soundcore              10016  3 snd
snd_page_alloc          9732  2 snd_intel8x0,snd_pcm
```

---

### Post by lorap on 2005-05-08
be i you i'd install VLC player.
no additional codecs needed and everything working fine.
try and you'll see.

---

