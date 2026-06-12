---
title: "totem, Resource busy or not availiable"
date: 2005-05-22
forum: General Help
---

### Post by abekat on 2005-05-22
Hi 

I'm having some problems launching totem. The error message states that "Resource busy or not availiable"

I've tried following the instructions in this link: [http://www.ubuntuforums.org/showthread.php?t=26567&highlight=totem](http://www.ubuntuforums.org/showthread.php?t=26567&highlight=totem)

Both lsof /dev/dsp and lsof /dev/snd/* come out empty, and sound server is disabled.

lsmod|grep snd gives:

snd_intel8x0           29984  1
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  0
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  2 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm


I'm not sure what soundcard is in (it's a laptop so it's probably some crap?). 

But totem worked before, actually it was the only sound application that worked untill I switched of the sound server.

I can play sound using xmms, so I'm guessing it's not the loudspeakers or the soundcard.

Any help would be appreciated.

regards
abekat

---

### Post by auburn on 2005-05-23
I get the same error. Sound works in mplayer, vlc. Everything, but totem.

---

