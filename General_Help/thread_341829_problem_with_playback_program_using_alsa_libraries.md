---
title: "problem with playback program using alsa libraries"
date: 2007-01-19
forum: General Help
---

### Post by tuvu on 2007-01-19
Hi,

I'm doing an audio project based on ALSA libraries. I'm trying to compile the "Minimal Playback Program" program on the tutorial [http://equalarea.com/paul/alsa-audio.html#playex](http://equalarea.com/paul/alsa-audio.html#playex) 

I did:

gcc mplay.c -lasound -o mplay
./mplay a.wav

and I got the error:
-------
```

ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM a.wav
cannot open audio device a.wav (No such file or directory)

```
-------

I can play a.wav smoothly using: aplay a.wav

I searched for a bit and it seems that the error is caused by some default setting, but I really dont know. Does anyone know how to fix this ? Thank you.

tuvu

---

