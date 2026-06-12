---
title: "controlling audio via ssh"
date: 2008-06-27
forum: General Help
---

### Post by jessika-kaos on 2008-06-27
In Gutsy I used to be able to control the audio output on my desktop via ssh. With Hardy and pulseaudio, something is different and I can't figure out how to make this work. When I log in and try to access any audio app I get errors:

```
sonne@rattatosk:~$ ssh -X sonne@#####.endoftheinternet.org
sonne@hive.endoftheinternet.org's password: 
sonne@HIVE:~$ alsamixer
*** PULSEAUDIO: Unable to connect: Connection refused

alsamixer: function snd_ctl_open failed for default: Connection refused
sonne@HIVE:~$ 
```

```
sonne@HIVE:~$ audacious
amidi-plug(amidi-plug.c:amidiplug_init:97): init, read configuration
amidi-plug(i_backend.c:i_backend_load:107): loading backend '/usr/lib/audacious/Input/amidi-plug/ap-fluidsynth.so'
amidi-plug(i_backend.c:i_backend_load:145): backend /usr/lib/audacious/Input/amidi-plug/ap-fluidsynth.so (name 'fluidsynth') successfully loaded

** (audacious:16242): WARNING **: Failed to connect to server: Connection refused
MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin
amidi-plug(i_backend.c:i_backend_unload:164): unloading backend 'fluidsynth'
amidi-plug(i_backend.c:i_backend_unload:167): backend 'fluidsynth' unloaded
sonne@HIVE:~$ 
```

I have made sure that I am added to the pulse-rt users group, and have enabled the network access and multicast in the pulseaudio options... what else do I need do I need to do to make this work?

(I'm not trying to transfer the audio over the network, I just want to control volume and my music as simply as possible)

---

### Post by sdennie on 2008-06-28
You could try switching all your sound to ALSA instead of Pulse Audio.  On the machine, if you have gnome on it, go to System->Preferences->Sound and switch everything to ALSA.

---

### Post by p_quarles on 2008-06-28
You might also change the output plugin in Audacious to pulseaudio.

---

