---
title: "Ubuntu 14.04 No sound after all fixes"
date: 2014-07-29
forum: General Help
---

### Post by briansykes on 2014-07-29
i just installed Ubuntu 14.04 and have run into a slight bit of a snag apparently, i've tried everything i can think of to find out why my sound doesn't work. Here is what i've tried so far:

alsamixer in terminal shows all up to max and unmuted (OO) aplay -l shows:

```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 11: HDMI 5 [HDMI 5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

alsa-info output is here: [http://www.alsa-project.org/db/?f=0b483fe75a288ab4acb16ba8799a08ada5d59737](http://www.alsa-project.org/db/?f=0b483fe75a288ab4acb16ba8799a08ada5d59737)

I selected the proper sound card in alsamixer as my NVidia hd audio, i'm currently not using the HDMI at all. As well as rebooting and seeing if that works, however when i try to do the alsa for-cereload i get this:

```
Unloading ALSA sound driver modules: snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer (failed: modules still loaded: snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-timer).
Loading ALSA sound driver modules: snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer.
```

I am so far at a complete loss as to what to do, my speakers worked fine, i literally just switched back to linux from windows after needing windows to play games, but i wanted linux back and now my sound refuses to work and the only thing i can see wrong is the alsa codecs not unloading. Any help would be very much appreciated. Also headphones do not work either.

Thanks in advance.

EDIT: It fixed itself somehow, no idea what the problem was but appears to be just fine now, much to my chagrin. O.o

---

