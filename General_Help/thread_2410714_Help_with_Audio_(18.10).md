---
title: "Help with Audio (18.10)"
date: 2019-01-19
forum: General Help
---

### Post by raeden2 on 2019-01-19
Hey all,

I'm experiencing an odd issue with my speakers on my line-out. I just installed 18.10 and my audio was working perfectly in youtube and my games. Randomly, or I'm not sure WHAT was installed to cause it, my audio started acting strangly. Music sounds just fine, as well as system sounds, however speech is incredibly muffled to the point I have to turn my speakers up very high in order to hear any of it. Even then, it sounds like the voices are in a fish bowl (best description I can come up with). Going into the Sound setting and performing an audio test on my speakers sounds just fine. Here's the output of my audio devices (issue is with 3):

pactl list short sinks
0    alsa_output.pci-0000_01_00.1.hdmi-stereo    module-alsa-card.c    s16le 2ch 44100Hz    SUSPENDED
1    alsa_output.usb-SteelSeries_SteelSeries_Arctis_7-00.analog-mono    module-alsa-card.c    s16le 1ch 44100Hz    SUSPENDED
2    alsa_output.usb-SteelSeries_SteelSeries_Arctis_7-00.analog-stereo    module-alsa-card.c    s16le 2ch 44100Hz    SUSPENDED
3    alsa_output.pci-0000_00_1f.3.analog-stereo    module-alsa-card.c    s16le 2ch 44100Hz    RUNNING

btw: My audio on the other devices sound just fine.

---

### Post by Frogs Hair on 2019-01-19
Support request, moved to *General Help*.

---

### Post by raeden2 on 2019-01-19
Update: It seems like all speech is trying to go through a center speaker which I don't have.. If I adjust the balance for my line-out then all speech works just fine (but only out of one speaker). My speaker setup is a 2.1 (left/right speakers + subwoofer).

---

