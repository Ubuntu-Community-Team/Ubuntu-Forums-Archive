---
title: "Audio Wont unmute"
date: 2018-05-19
forum: General Help
---

### Post by simon114 on 2018-05-19
Good Evening,
 Im running Ubuntu 16.04, when booting up and getting to the login screen I hear the ubuntu bongo sound, then I log in and audio is muted (greyed out) and no audio device is in the system settings/sound section
I have run

 ```
[COLOR=#393939][FONT=Consolas]aplay -l[/FONT][/COLOR]
```

with the result being 

```
**** List of PLAYBACK Hardware Devices ****card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 0: ALC269VC Analog [ALC269VC Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

So out of curiosity I logged in as a guest user and audio works fine,

This happened whilst editing an audio file in audacity.

Any help would be much appreciated.

---

### Post by simon114 on 2018-05-19
Solved the issue with this command 

sudo mv ~/.config/pulse ~/.config/pulse.old

---

