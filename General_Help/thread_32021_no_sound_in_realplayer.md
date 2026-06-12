---
title: "no sound in realplayer"
date: 2005-05-05
forum: General Help
---

### Post by dukeinlondon on 2005-05-05
I've got sound working fine but somehow, real player complains that the sound device is busy.... I suppose that thing is looking for /dev/dsp but there is nothing like that on my system. 
here are the sound modules loaded (and working) on my system

```
snd_emu10k1            81668  4
snd_rawmidi            22944  1 snd_emu10k1
snd_seq_device          8332  2 snd_emu10k1,snd_rawmidi
snd_ac97_codec         64608  1 snd_emu10k1
snd_pcm                84872  3 snd_emu10k1,snd_ac97_codec
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  2 snd_emu10k1,snd_pcm
snd_util_mem            4608  1 snd_emu10k1
snd_hwdep               9220  1 snd_emu10k1
snd                    50276  14 snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm,snd_timer,snd_hwdep
```

could it be related to alsa oss emulation not loaded ? How do I load it if this is the case ?

thanks in advance

---

### Post by poofyhairguy on 2005-05-05
[QUOTE=dukeinlondon]I've got sound working fine but somehow, real player complains that the sound device is busy.... I suppose that thing is looking for /dev/dsp but there is nothing like that on my system. 
here are the sound modules loaded (and working) on my system

```
snd_emu10k1            81668  4
snd_rawmidi            22944  1 snd_emu10k1
snd_seq_device          8332  2 snd_emu10k1,snd_rawmidi
snd_ac97_codec         64608  1 snd_emu10k1
snd_pcm                84872  3 snd_emu10k1,snd_ac97_codec
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  2 snd_emu10k1,snd_pcm
snd_util_mem            4608  1 snd_emu10k1
snd_hwdep               9220  1 snd_emu10k1
snd                    50276  14 snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm,snd_timer,snd_hwdep
```

could it be related to alsa oss emulation not loaded ? How do I load it if this is the case ?

thanks in advance[/QUOTE]



[http://ubuntuforums.org/showthread.php?t=25548&highlight=audio](http://ubuntuforums.org/showthread.php?t=25548&highlight=audio)

[http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567)

---

### Post by dukeinlondon on 2005-05-06
Excellent, thanks

---

