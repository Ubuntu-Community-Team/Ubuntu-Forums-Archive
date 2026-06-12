---
title: "crackling Jack+PuseAudio(Alsa)"
date: 2017-01-02
forum: General Help
---

### Post by lucedan on 2017-01-02
Hello.

Recently I connected Ardour's outputs to other software in Ubuntu 16.10.
To do this, I had to install:

apt-get install pulseaudio-module-jack

I didn't touch the file /etc/pulse/default.pa , as 

load-module module-jack-sink
load-module module-jack-source

were creating some problems, and the file couldn't load appropriately.

Now, Ardour and other applications are connected, but anytime I start JACK, I have a lot of crackling whenever streaming sounds.
Can you suggest me ideas to solve this problem?

Luca

---

