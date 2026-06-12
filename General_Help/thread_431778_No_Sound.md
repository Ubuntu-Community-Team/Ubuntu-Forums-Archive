---
title: "No Sound"
date: 2007-05-03
forum: General Help
---

### Post by sv452 on 2007-05-03
Hi all...

i have a very wierd problem -

i have no sound but when i am in terminal i can hear my speaker beep ... but there is no sound when i test for either alsa, oss, esd, autodetect.... but i don't get errors either... my volume is turned up all the way ...

this is my lsmod output

```
snd_intel8x0           34844  3 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  2 snd_pcm_oss
snd_pcm                84612  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  2 snd_pcm
snd                    58372  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  2 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
```

when i try speaker-test i get the following
```
speaker-test 1.0.11

Playback device is ICH5
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM ICH5
Playback open error: -2,No such file or directory
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM ICH5
Playback open error: -2,No such file or directory
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM ICH5
Playback open error: -2,No such file or directory
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM ICH5
Playback open error: -2,No such file or directory
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM ICH5
Playback open error: -2,No such file or directory
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM ICH5
Playback open error: -2,No such file or directory

```

i use edgy.

thanx

---

