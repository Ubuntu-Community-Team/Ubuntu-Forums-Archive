---
title: "Sound will not stay after reboot"
date: 2015-01-13
forum: General Help
---

### Post by ronbrooks on 2015-01-13
My sound card is ok and is listed in the computer, but will not work until I run sudo alsa force-reload and this is the message I get when I run that command.
Terminating processes: 1118 1984
1984.
/sbin/alsa: Warning: Processes using sound devices: 6539(pulseaudio). 
Unloading ALSA sound driver modules: snd-hda-intel snd-hda-codec-realtek snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer (failed: modules still loaded: snd-hda-intel snd-hda-codec-realtek snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-timer).
Loading ALSA sound driver modules: snd-hda-intel snd-hda-codec-realtek snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer.

When I do the sound works fine but after a restart the sound quits and I get dummy output from the sound settings.  

Can someone help me with getting this setting to stay after a reboot. 

I am using Ubuntu 14.04

---

