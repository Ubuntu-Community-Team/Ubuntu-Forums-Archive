---
title: "No sound (Partly sorted) YouTube won't play on APU?"
date: 2014-08-23
forum: General Help
---

### Post by fantasma3 on 2014-08-23
Hi All

I just installed Lubuntu 14.04 64Bit on my new HTPC and now I'm having some problems.

First of: I run an AMD Athlon 5350 with the Proprietary drivers from the Aditional Drivers option.

First issue: I found, my sound didn't work at all. (First time I experienced this issue with Linux (But seems like people have(are) dealt(dealing) with it.))
I changed the ~/.asoundrc file to take my analog device as default and now I have sound on both Audacious and XBMC, but that's it. No sound from Youtube (If that even works (see Problem 2)) and no sound from steam games.
> XXX@HTPC:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Generic [HD-Audio Generic], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
So I changed the ~/.asoundrc to 

> pcm.!default {
    type hw
    card 1
}
ctl.!default {
    type hw
    card 1
}



I tried a whole bunch of things I found on the internet, for instance re-installed alsa/pulseaudio, nothing seems to work.


Second issue: Youtube doesn't work. (Most frustrating since I have the same issue on Windows 7 (64Bit) but couldn't resolve it.)

I go to YouTube, click any video I want, the add plays, the video starts playing, stops after 1 second, starts switching to all possible resolutions, then says "An error occured, try again."
I assume I have the best drivers available and the APU should be fast enough since I could do it with an Atom330/ION.


If you need more info, I'll be free to give you all the info you want.

Thanks in advance

---

