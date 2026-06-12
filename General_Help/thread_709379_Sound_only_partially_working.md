---
title: "Sound only partially working"
date: 2008-02-27
forum: General Help
---

### Post by jschaab on 2008-02-27
Hi,
  I'm running a recent install of Xubuntu 7.10. Currently some of my applications can play sound (pidgeon, vlc) and I get a login sound. They can even play sound at the same time. for instance if I'm playing an MP3 with vlc pidgeon can still play sounds too... However some programs still can't play sound. particularly anything that trys to use the command "play". I've noticed I get the following error if I use play directly:
```

jschaab@jschaab-desktop:~$ which play
/usr/bin/play
jschaab@jschaab-desktop:~$ play /usr/share/sounds/purple/receive.wav
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
play stio: Failed writing default: cannot open audio device

```

also aplay:
```

jschaab@jschaab-desktop:~$ which aplay
/usr/bin/aplay
jschaab@jschaab-desktop:~$ aplay /usr/share/sounds/purple/receive.wav
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
aplay: main:545: audio open error: Device or resource busy

```

I've also noticed the wine configure tool always fails the audio test, no matter which option I choose.

---

### Post by nuclearpidgeon on 2008-04-08
Move to Multimedia and Video

---

