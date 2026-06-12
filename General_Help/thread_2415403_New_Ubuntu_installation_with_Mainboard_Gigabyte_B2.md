---
title: "New Ubuntu installation with Mainboard Gigabyte B250M No Sound"
date: 2019-03-25
forum: General Help
---

### Post by freelensia on 2019-03-25
Hello,

I just installed Ubuntu 18.04 dual boot with Windows 10 on a Mainboard Gigabyte B250M.

The external speakers work well in Windows via Realtek Sound Control Panel.

In Linux however I am completely new to setting things up.

My Alsa log:
[http://alsa-project.org/db/?f=7f9e463b6e3cc950a1cac13c2b422e1a4cf95fd1](http://alsa-project.org/db/?f=7f9e463b6e3cc950a1cac13c2b422e1a4cf95fd1)

My aplay -l results:
```
ducpham@nlt-B250-FinTech:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

What should I do next to get the sound working?

Thank you.

---

