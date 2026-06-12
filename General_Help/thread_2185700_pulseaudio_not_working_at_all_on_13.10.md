---
title: "pulseaudio not working at all on 13.10"
date: 2013-11-03
forum: General Help
---

### Post by tyklink on 2013-11-03
after upgrading to 13.10, pulseaudio isnt recognizing ANY of my sound outputs or inputs, i try to open pavucontrol and it says it cannot connect to pulseaudio, and finally theres not even a volume indicator up top anymore... ive tried everything i can think of (reloading alsa and even re-installing pulseaudio) and absolutely nothing is working... anybody have any ideas? i am currently running 64bit 13.10 and my sound chip is a realtek alc888

---

### Post by Yellow Pasque on 2013-11-03
Try resetting the user config files (the package manager doesn't touch these files) and restarting pulse:
```
rm -r ~/.config/pulse; pulseaudio -k
```

---

### Post by tyklink on 2013-11-03
tried that too actually when i looked through that sticky... still didnt work >_<

---

### Post by Yellow Pasque on 2013-11-03
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
[https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)

---

### Post by tyklink on 2013-11-05
[http://www.alsa-project.org/db/?f=163c45c226826ffbe9647f87eaceb902bc7346d8](http://www.alsa-project.org/db/?f=163c45c226826ffbe9647f87eaceb902bc7346d8)

and the pulse audio log thing isnt working

---

