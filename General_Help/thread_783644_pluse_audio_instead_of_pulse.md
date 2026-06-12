---
title: "pluse audio instead of pulse"
date: 2008-05-05
forum: General Help
---

### Post by guythatsits on 2008-05-05
Hi, This is my first time ever posting to a forum even though i read many. I have searched for my problem all over google and the ubuntu forum for 2 days and either i suck at finding solutions or this problem hasn't existed yet. I just fear the flaming i will get if there is a post already, so here it goes. I have a asus p5w motherboard with realtek audio 7.1. Pulseaudio seems to be working ok for most apps except wine. Also i was trying to run speaker-test and i keep getting the same errors in the terminal. I am sure it is some sort of easy fix. I am using a fresh install of Hardy its only a few days old and i haven't really changed any of the default settings yet. 


Here is the output of wine when i go to the audio panel of winecfg
ALSA lib dlmisc.c:118:(snd_dlsym_verify) unable to verify version for symbol _snd_pcm_pluse_open
ALSA lib pcm.c:2109:(snd_pcm_open_conf) symbol _snd_pcm_pluse_open is not defined inside /usr/lib/alsa-lib/libasound_module_pcm_pluse.so
ALSA lib dlmisc.c:118:(snd_dlsym_verify) unable to verify version for symbol _snd_pcm_pluse_open
ALSA lib pcm.c:2109:(snd_pcm_open_conf) symbol _snd_pcm_pluse_open is not defined inside /usr/lib/alsa-lib/libasound_module_pcm_pluse.so
preloader: Warning: failed to reserve range 00000000-60000000

I have tried doing a reinstall of libasound2 
i just don't know why pulse is spelled wrong in all of the errors.


I am willing to give you any kind of feedback you need. I know nothing of linux really but if you direct me i will do my best. 
Thanks for you time and effort!
Bryan

Actually the first error i had was:
ALSA lib pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_pluse.so
ALSA lib pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_pluse.so
but i figured i would be slick and add a symbolic link to the actual file... which produced the other error

The actual file /usr/lib/alsa-lib/libasound_module_pcm_pulse.so is there... so i really don't have a clue what is up. I figured there was a config file somewhere but alas i haven't found it.

---

