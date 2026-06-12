---
title: "Microphone no longer works in most programs"
date: 2019-01-26
forum: General Help
---

### Post by cranerja on 2019-01-26
I have been using one of the generic Amazon microphones for over a year. Yesterday, it started behaving strangely:
Audacity: It monitors the mic in a 'chunky' fashion(gifs below) and plays back recordings at chipmunk speed.
Discord: Provides the same sound that audacity records for one second and then stops working.
OBS: Works fine.
Settings: Before opening audacity, it shows the graph normally. After, it shows it 'chunky'. (gifs below)
Here is the mic info:
```
$ pactl list short sinks

0 alsa_output.pci-0000_00_1f.3.analog-stereo module-alsa-card.c s16le 2ch 44100Hz RUNNING


```

Before/After Audacity:
[https://i.imgur.com/eS1Dxxj.gif](https://i.imgur.com/eS1Dxxj.gif)

[https://i.imgur.com/5tppBee.gif](https://i.imgur.com/5tppBee.gif)

---

