---
title: "No Audio through Thunderbolt 3/HDMI on Dell XPS 9560 Developer's Edition"
date: 2017-10-28
forum: General Help
---

### Post by d3p74 on 2017-10-28
Hello

I have been having problems with HDMI audio-out on a Dell XPS 13 laptop (Developer Edition). 

It's running Ubuntu 17.04 with 4.10.1-041001-generic kernel. 

```
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty

```

```
uname -a
Linux void 4.10.1-041001-generic #201702260735 SMP Sun Feb 26 12:36:48 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

I'm using xfce4 4.12 distributed by Xubuntu


The GPU is Intel(R) HD Graphics 620. 


I have been able to get HDMI audio to work on the external monitor, but only by using Mirror Displays in the Display Settings... However, using this setting initially sets my resolution to 1680x1050 instead of 1920x1080. I can get 1920x1080 resolution for a while, but at some point the audio will fail to play through HDMI, and play from the laptop speakers once I set the Pulse Audio configuration to Analog Stereo Duplex

I would like to use my external monitor as my default/main display, with audio. 

Any ideas about what I need to do to troubleshoot this?

---

