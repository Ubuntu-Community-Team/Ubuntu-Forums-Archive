---
title: "Multiple Sounds at Once"
date: 2007-09-15
forum: General Help
---

### Post by netelemental on 2007-09-15
Hey,
I know that this topic has been run into the ground multiple times already, but none of the things I've tried have worked so I'm going to try posing the question on my own - 

I have 2 sound cards - one builtin to the motherboard, and the other a C-Media PCI card. I'm attempting to get multiple sounds to play at once. I've got ALSA set up and I can play a single sound at a time through alsa, although recently after I rebooted I can't even play sounds on normal applications, just the test under sound preferences or gstreamer-properties. When I run gstreamer-properties, I get the following in the terminal:
```

jmeady@ubuntu:~$ gstreamer-properties
- using device default
- using device default
ALSA lib pcm_dmix.c:831:(snd_pcm_dmix_open) unable to create IPC semaphore
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'
- using device default
- using device default
ALSA lib pcm_dmix.c:831:(snd_pcm_dmix_open) unable to create IPC semaphore
- using device default
- using device default
ALSA lib pcm_dmix.c:831:(snd_pcm_dmix_open) unable to create IPC semaphore
- using device default
- using device default
ALSA lib pcm_dmix.c:831:(snd_pcm_dmix_open) unable to create IPC semaphore

```

Any ideas? I can provide any files or output you feel is necessary.

Thanks, 
NetElemental

---

