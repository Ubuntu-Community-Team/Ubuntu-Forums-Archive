---
title: "Mic is not working under Skype"
date: 2006-11-11
forum: General Help
---

### Post by Lucy on 2006-11-11
Moin,moin

under skype 1.3 the microphone is not working correctly. 
When I use the Skype test call functioanlity my recorded voice sounds metallic and has a very low volume. 

Audacity and skype under windows works nicely. 

I have a soundblaster audigy SE

I tried OSS and ALSA but the symptoms stays the same.

Thx

---

### Post by krismatth3 on 2006-11-11
Most likely one of the mixer settings are muted. Open up the mixer applet and look at all the options - for all devices (it will sometimes list two, different mixers on the same card).

---

### Post by poekie on 2006-11-26
I also have Soundblaster audigy SE, but I can't even get the mic to work.. I use CA0106 as a driver, but that just lists less options in mixer than the normal (standard) driver.
I have been thinking of going back to the standard driver, as I actually used the CA0106driver as a way to get 5.1 surround sound, but in three months, I still don't have that working.. And now my mic seems to have joined in the fun of non-working..

---

### Post by adas on 2006-11-30
When I run a skype in terminal a have this command:
> ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2143:(snd_pcm_open_noupdate) Unknown PCM dmix:CMI8738MC6
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2143:(snd_pcm_open_noupdate) Unknown PCM dmix:CMI8738MC6
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2143:(snd_pcm_open_noupdate) Unknown PCM dmix:CMI8738MC6
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2143:(snd_pcm_open_noupdate) Unknown PCM dmix:CMI8738MC6


I have a Sound Card CMI 8738

When I Run a: gnome-sound-properties

```
adam@adas:~$ /usr/bin/gnome-sound-properties

(gnome-sound-properties:4755): Gnome-WARNING **: Accessibility: failed to find module 'libgail-gnome' which is needed to make this application accessible
GTK Accessibility Module initialized

(gnome-sound-properties:4755): Gnome-WARNING **: Accessibility: failed to find module 'libatk-bridge' which is needed to make this application accessible
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2143:(snd_pcm_open_noupdate) Unknown PCM dmix:CMI8738MC6

```

---

### Post by adas on 2006-11-30
I forget write this: Xubuntu 6.10, my integrated sound card is disable. Sound works fine in eg. quodlibet.

---

