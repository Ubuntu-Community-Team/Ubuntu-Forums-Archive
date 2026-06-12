---
title: "Sound Problem"
date: 2016-01-08
forum: General Help
---

### Post by alan41 on 2016-01-08
What information do I have to post and where please:

I have no sound through my HDMI to my monitor.

The monitor is working ok as it is a dual boot PC with the  other o/s being Windows 10

I have just built this PC using an ASrock B150M-HDV Motherboard with a Intel i3 processor.

---

### Post by QDR06VV9 on 2016-01-08
```
sudo apt-get install pavucontrol

```

PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume
control tool (mixer) for the PulseAudio sound server. In contrast to
classic mixer tools _**this one allows you to control both the volume of**_
_**hardware devices and of each playback stream separately. It also allows**_
_**you to redirect a playback stream to another output device**_ without
interrupting playback.

---

### Post by alan41 on 2016-01-08
> **runrickus said:**
> ```
sudo apt-get install pavucontrol

```

PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume
control tool (mixer) for the PulseAudio sound server. In contrast to
classic mixer tools _**this one allows you to control both the volume of**_
_**hardware devices and of each playback stream separately. It also allows**_
_**you to redirect a playback stream to another output device**_ without
interrupting playback.

This is already installed and I have selected the Output as HDMI but still no sound

---

### Post by QDR06VV9 on 2016-01-08
The app or player also has to be pointed to the HDMI output ..
What is the output of this
```
[COLOR=#000000][FONT=Ubuntu Mono]aplay -l[/FONT][/COLOR]
```

---

### Post by alan41 on 2016-01-10
> **runrickus said:**
> ```
sudo apt-get install pavucontrol

```

PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume
control tool (mixer) for the PulseAudio sound server. In contrast to
classic mixer tools _**this one allows you to control both the volume of**_
_**hardware devices and of each playback stream separately. It also allows**_
_**you to redirect a playback stream to another output device**_ without
interrupting playback.

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: ID 2809 Digital [ID 2809 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

> **runrickus said:**
> The app or player also has to be pointed to the HDMI output ..
What is the output of this
```
[COLOR=#000000][FONT=Ubuntu Mono]aplay -l[/FONT][/COLOR]
```

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: ID 2809 Digital [ID 2809 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by pqwoerituytrueiwoq on 2016-01-10
[http://ubuntuforums.org/showthread.php?t=2273289](http://ubuntuforums.org/showthread.php?t=2273289)
seems relevant to you
how i found that:
motherboard model -> spec sheet -> get audio chip -> google -> find solution

---

