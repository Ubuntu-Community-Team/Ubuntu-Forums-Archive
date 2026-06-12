---
title: "Sound: only have headphone option in the switches tabof volume control"
date: 2007-12-16
forum: General Help
---

### Post by agerg on 2007-12-16
Hi all...One of a number of problems after installing Gutsy (the biggest being that I am totally new to linux) is that sound will only play through my headphones, and in the switches tab in volume control there is only that option to tinker with...this is what I get if I type
"aplay -l" into terminal:
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
I visited some other threads,following advice and installed things like esound, I have also tried:
```
sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source
```
and am told I have the latest version but when I try:
```
sudo dpkg-reconfigure alsa source
``` (because these are a series of steps someone suggested) It tells me alsa isn't installed :confused:

as will be blatantly obvious I don't know what I'm doing yet but suffice it to say that unless my speakers got destroyed the instant I installed ubuntu, I haven't a clue what's going on. Can anyone help?

---

