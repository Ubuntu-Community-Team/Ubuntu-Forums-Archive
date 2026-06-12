---
title: "Programmatically choosing application-specific PulseAudio input?"
date: 2013-07-07
forum: General Help
---

### Post by pokepal101 on 2013-07-07
Okay: what I want to do is record my desktop Dxtory style, with video, microphone and 'stereo mix' each on separate tracks.

I can accomplish this, but it's not a very 'nice' solution. My bash script looks like this, currently:
```
#!/bin/sh
pavucontrol &
gnome-terminal -e "ffmpeg -f x11grab -r 30 -s 1600x900 -i :0.0 $1.0.mkv"
gnome-terminal -e "ffmpeg -f alsa -i pulse $1.1.wav"
gnome-terminal -e "ffmpeg -f alsa -i pulse $1.2.wav"
```

It works, but it requires me to manually select, in pavucontrol, which audio source I want each ffmpeg process to record.

My question is: can I programmatically select this in the bash script? Some thing like this:
```
set-pulseaudio-source "Built-in Audio Analog Stereo"
gnome-terminal -e "ffmpeg -f alsa -i pulse $1.1.wav"
set-pulseaudio-source "Monitor of Built-in Audio Analog Stereo"
gnome-terminal -e "ffmpeg -f alsa -i pulse $1.1.wav"
```

Thanks in advance.

---

