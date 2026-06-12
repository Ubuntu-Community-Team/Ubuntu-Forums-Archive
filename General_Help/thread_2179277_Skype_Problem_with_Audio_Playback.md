---
title: "Skype: Problem with Audio Playback"
date: 2013-10-07
forum: General Help
---

### Post by M1GEO on 2013-10-07
Hello folks.

I have searched around a bit regarding this issue, but cannot find an answer or find an answer which is a bit crude.  They typically resort to removing Pulse Audio, which I don't really want to do since everything else works great with it (Bluetooth headphones, etc).

The basic issue is that I cannot get any sound out of Skype, and when run in a terminal, it gives a good few errors relating to pulse audio.  Any advice or pointers would be greatly received:

```
george@marconi:~$ skype
ALSA lib conf.c:4687:(snd_config_expand) Unknown parameters CARD=PCH
ALSA lib control.c:951:(snd_ctl_open_noupdate) Invalid CTL default:CARD=PCH
ALSA lib conf.c:4687:(snd_config_expand) Unknown parameters CARD=PCH
ALSA lib control.c:951:(snd_ctl_open_noupdate) Invalid CTL default:CARD=PCH
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
*** Error in `skype': corrupted double-linked list: 0xdf742ff8 ***

```

A couple of images too:

[Image 1]("https://www.dropbox.com/s/7jwm1y8f5f31vba/Skype_audio1.png")
[Image 2]("https://www.dropbox.com/s/p4myrybx7h50af1/Skype_audio2.png")

I am familiar with the pavucontrol software and generally how sound works on Linux, so I guess I'm missing something.  I have tried just using the "default (default)" audio settings and using pavucontrol to link up the rest, I have tried directly using the hardware, and ALSA.  All just award me an immediate failure on Skype.

Thanks for your time in reading.

George

---

