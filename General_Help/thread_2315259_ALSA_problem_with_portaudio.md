---
title: "ALSA problem with portaudio?"
date: 2016-02-27
forum: General Help
---

### Post by silvio9 on 2016-02-27
Hi guys I'm trying to test a program that is intended to pick up a signal from the microphone and give me a result. I'm using portaudio and when I compile I get the following errors (to be said that I tried many guides online but nothing worked yet):
ALSA lib pcm_dsnoop.c:618:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:1022:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111) 
bt_audio_service_open: connect() failed: Connection refused (111)
ALSA lib pcm_dmix.c:1022:(snd_pcm_dmix_open) unable to open slave
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Opening default

Anyone has an idea of what could be the cause? I read that need to open jackd2 but no difference, also tried to pause portaudio using pasuspender. Once again no difference. Thanks in advance for your help

---

