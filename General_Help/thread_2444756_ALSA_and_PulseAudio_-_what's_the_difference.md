---
title: "ALSA and PulseAudio - what's the difference?"
date: 2020-06-03
forum: General Help
---

### Post by GhX6GZMB on 2020-06-03
As the title says: which should I prefer? I don't quite understand the difference between the two, and am not a specialist on audio.
Comments and suggestions are very welcome.

Thanks.

---

### Post by TheFu on 2020-06-03
On my systems, PulseAudio controls the underlying ALSA setup.  After 12+ yrs of work, pulse on Ubuntu is finally starting to be more useful than directly dealing with ALSA config files.  My friends who use other distros (Fedora mainly) haven't had Pulse issues for 5+ yrs. They claim it is Ubuntu, but it could just be me.  Wouldn't be the first time i was "special". ;)

As proof, I offer this command on a 16.04 minimal desktop:
```
$ pactl list short sinks
4       **alsa**_output.pci-0000_0a_00.3.analog-stereo      module-alsa-card.c     s16le 2ch 44100Hz        SUSPENDED
```

pactl is a CLI PulseAudio control program.
Note that the sink has "alsa" in the name?

Looking at "sources" ... microphones: 
```
$ pactl list short sources
4       alsa_output.pci-0000_0a_00.3.analog-stereo.monitor      module-alsa-card.c      s16le 2ch 44100Hz       SUSPENDED
6       **alsa**_input.usb-046d_HD_Pro_Webcam_C920_76B4D93F-02.analog-stereo       module-alsa-card.c       s16le 2ch 32000Hz       IDLE
```

The analog-stereo.monitor input is where we can listen as an audio "monitor" would.  Sources and Sinks have names. Those names are how PulseAudio is told what goes with which program as inputs and outputs.

Clear as mud?

---

### Post by poorguy on 2020-06-03
These may be useful.

[https://linuxhint.com/guide_linux_audio/](https://linuxhint.com/guide_linux_audio/)

[https://linuxhint.com/pulse_audio_sounds_ubuntu/](https://linuxhint.com/pulse_audio_sounds_ubuntu/)

[https://www.maketecheasier.com/pulse-audio-equalizer-ubuntu/](https://www.maketecheasier.com/pulse-audio-equalizer-ubuntu/)

[https://www.maketecheasier.com/alsa-utilities-manage-linux-audio-command-line/](https://www.maketecheasier.com/alsa-utilities-manage-linux-audio-command-line/)

---

### Post by CatKiller on 2020-06-03
The hardware side is handled by ALSA. The software side is handled by PulseAudio. You use both.

ALSA used to also have a software side that had some big limitations; that's the part that got replaced by PulseAudio.

---

### Post by HermanAB on 2020-06-04
Pulse Audio was very buggy in the beginning which gave it a bad reputation, but nowadays it works very well indeed.  

Pulse Audio is the layer that allows you to plug multiple audio devices (Built-in audio, Wired Headset, Bluetooth Headset, MP3 player, Web video/audio streaming) into your machine and have them all work happily together at the same time or severally.  With ALSA only, it is a manual configuration head-ache.

---

