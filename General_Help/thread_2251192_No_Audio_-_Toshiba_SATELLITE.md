---
title: "No Audio - Toshiba SATELLITE"
date: 2014-11-02
forum: General Help
---

### Post by jeff103 on 2014-11-02
Hi There,


Just did a fresh install of lubuntu 14.10. Everything works great, except for the Audio.


Running on Toshiba SATELLITE U205-S5002. I did some research and have installed pavucontrol and verified that pavucontrol, pulseaudio, pulseaudio-utils and libgtk-3-0 are installed.

I launched PulseAudio Volume Control, and noticed that in Output Devices tab > Port, I see two options "Speakers (unavailable)" and "Headphones (plugged in)". The headphones are not plugged in. If I do plug the headphones in, the sound works great, but of course I would like to use the speakers on the laptop.

Results of command aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD1981 Analog [AD1981 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1

  Subdevice #0: subdevice #0

Also, in PulseAudio's configuration tab, for Built-in Audio, i tried switching back and forth between Analog Stereo Output and Analog Stereo Duplex, but no luck.

Anything else I can give you guys to help get this resolved, let me know. Thanks a bunch :)

---

