---
title: "How to setup pulseaudio under i3?"
date: 2016-03-11
forum: General Help
---

### Post by Tadaen_Sylvermane on 2016-03-11
I've installed the server 14.04, all my packages. Using i3 and have it all configured. However sound is proving difficult at best. Pavucontrol only shows "Dummy Output". Pacmd and pactl show the same thing. I have tried a few things I found on google, nothing working yet. Pulse refuses to seee anything othern than a Dummy output.

cat /proc/asound/cards is showing both my hdmi and pch sound  cards but pulse wont see them. What am I missing?

---

### Post by Tadaen_Sylvermane on 2016-03-11
I figured it out right after I posted. The solution for anyone who may try switching to a simple WM for the first time was 2 fold.

First I had to add my user to the audio group ( did video as well for good measure).
Second I had to make pulseaudio start properly at launch of i3. I did so as such in my ~/.i3/config

```
exec --no-startup-id i3-msg 'exec /usr/bin/pulseaudio --start'
```

And last but not least to get the volume keys working on the output device by itself and not just in VLC I wrote a simple script and mapped it to keybinds in my ~/.i3/config

```
#!/bin/bash
 
ACTIVESYNC=$(pacmd list-sinks | grep \* | awk '{print $3}')

case "$1" in
    raise)
         pactl set-sink-volume "$ACTIVESYNC" +5%
         ;;
    lower)
         pactl set-sink-volume "$ACTIVESYNC" -- -5%
         ;;
    mute)
         pactl set-sink-mute "$ACTIVESYNC" toggle
         ;;
esac
```

---

