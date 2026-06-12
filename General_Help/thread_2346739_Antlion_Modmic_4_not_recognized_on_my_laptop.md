---
title: "Antlion Modmic 4 not recognized on my laptop"
date: 2016-12-18
forum: General Help
---

### Post by kindlyfire on 2016-12-18
I'm running Kubuntu and my Antlion Modmic 4 doesn't get recognized. Can somebody help me with it ?

```
 $ aplay --list-devices
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: PCH [HDA Intel PCH], device 0: ALC3236 Analog [ALC3236 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ cat /proc/asound/devices
  1:        : sequencer
  5: [ 0]   : control
  6: [ 0- 3]: digital audio playback
  7: [ 0- 7]: digital audio playback
  8: [ 0- 8]: digital audio playback
  9: [ 0- 0]: hardware dependent
 10: [ 2]   : control
 11: [ 2- 0]: digital audio playback
 12: [ 2- 0]: digital audio capture
 13: [ 2- 0]: hardware dependent
 33:        : timer

$ lspci -v | grep -i audio
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
        Subsystem: ASUSTeK Computer Inc. Haswell-ULT HD Audio Controller
00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)
        Subsystem: ASUSTeK Computer Inc. 8 Series HD Audio Controller 
```

I have an internal mic as well as a Hyper X Cloud 2 headset (the mic of the headset gets recognized). While running these commands my headset was disconnected and the Modmic was plugged in.

---

