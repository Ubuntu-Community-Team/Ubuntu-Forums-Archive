---
title: "On my Lenovo S205, there is no audio"
date: 2013-11-17
forum: General Help
---

### Post by andrewnguyen2010 on 2013-11-17
I installed lubuntu and ubuntu, but both didn't have audio on it At first I thought I needed a driver, but i can't find it. I had another thread which no one responded and one person told me to type this in terminal
```
aplay -l
```
and i got
```
**** List of PLAYBACK Hardware Devices ****card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: CX20590 Analog [CX20590 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
Please Help

---

### Post by grier-devon on 2013-11-17
Try this and let me know

```
[FONT=Ubuntu Mono]killall pulseaudio[/FONT]
```

---

