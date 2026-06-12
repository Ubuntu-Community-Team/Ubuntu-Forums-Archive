---
title: "No Playback in Ubuntu 14.04.2"
date: 2015-07-12
forum: General Help
---

### Post by mkayel on 2015-07-12
The microphone seems to be working, it's detected, I've got 4 audio outputs and they're not responsive. I tested all four, I still get no sound.

Here's my Audio info:
[http://www.alsa-project.org/db/?f=123eb0a15a0ea75c27de5ed7fa64a9c246f516a1](http://www.alsa-project.org/db/?f=123eb0a15a0ea75c27de5ed7fa64a9c246f516a1)

Note: The commands completely wreck my system. The System Settings icon disappear.
```
sudo apt-get remove --purge alsa-base pulseaudio
sudo apt-get install alsa-base pulseaudio
```

Thank you.

---

