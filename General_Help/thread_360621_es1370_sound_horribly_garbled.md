---
title: "es1370 sound horribly garbled"
date: 2007-02-13
forum: General Help
---

### Post by lunatic77 on 2007-02-13
I rarely use my sound card, so I am not exactly sure when it was broken.  I do remember using it just fine in Dapper, but I have upgraded to Edgy a few months ago.  Now, any sound coming from my sound card (wav, mp3, etc.) is garbled and makes weird screeching noises, mixed in with almost intelligible audio.  I have found no other posts or anything on Google to help out with this.  

from lspci:
```
00:09.0 Multimedia audio controller: Ensoniq ES1370 [AudioPCI]
        Subsystem: Unknown device 4942:4c4c
        Flags: bus master, slow devsel, latency 32, IRQ 9
        I/O ports at 9400 [size=64]
```

from lsmod | grep snd:
```
snd_ens1370            22176  1 
gameport               17160  1 snd_ens1370
snd_rawmidi            27264  1 snd_ens1370
snd_seq_device          9868  1 snd_rawmidi
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  2 snd_ens1370,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd_ak4531_codec        9984  1 snd_ens1370
snd                    58372  10 snd_ens1370,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_ak4531_codec
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_ens1370,snd_pcm
```

Thanks in advance for any help!!!!!!!

---

