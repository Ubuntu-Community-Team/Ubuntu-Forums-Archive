---
title: "Why doesn't the sound work through HDMI on my NUC?"
date: 2017-02-25
forum: General Help
---

### Post by ianberg on 2017-02-25
I have a new Kaby lake NUC running on Ubuntu 16.1. HDMI is listed as an option in 'Sound Settings' and if I open pavucontrol I can see the 'sound monitor bar' flickering up and down when I play a youtube video, but no sound comes out of my TV. The headphone jack works fine.

The only thing I can think this might be is because this is an older TV and could be using HDMI 1, not HDMI 2.

```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC255 Analog [ALC255 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I also went through speaker-test and manually tried each device but can't get a test tone through any of the devices.

e.g.
```

speaker-test -D hdmi:CARD=PCH,DEV=1 -c 2
```

I also tried the above command but manually selecting two frequencies I'm sure the TV accepts.

cat /proc/asound/car*/co* | grep Codec outputs.

```
 Codec: Realtek ALC255 Codec: Intel Kabylake HDMI
```


edit: The manual hints that the TV uses HDMI 1.3 at least, since it requests a cable of that spec or higher

Any help is appreciated. P.S wasn't sure if this counted as multimedia or not

---

