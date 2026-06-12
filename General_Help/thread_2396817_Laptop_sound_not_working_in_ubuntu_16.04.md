---
title: "Laptop sound not working in ubuntu 16.04"
date: 2018-07-21
forum: General Help
---

### Post by kyuhyong on 2018-07-21
I installed ubuntu 16.04 on a gaming laptop which is similar to following link [http://www.clevo.com/clevo_prodetail.asp?id=1109&lang=en](http://www.clevo.com/clevo_prodetail.asp?id=1109&lang=en)
Everything works just fine except sound. I only can hear sound from Bluetooth. 

I think I almost tried everything available on the internet but nothing seems to work. 
Reinstalling alamixer, pulseaudio etc..
Is there any other options that I can try?

---

### Post by kyuhyong on 2018-07-23
Here is the list of attached sound cards. 

$ aplay -l**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC1220 Analog [ALC1220 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC1220 Digital [ALC1220 Digital]
  Subdevices: 1/1
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
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

And to figure out  [COLOR=#333333][FONT=Ubuntu]which model of sound card I am using,
[/FONT][/COLOR]
 $ cat /proc/asound/card0/codec* | grep CodecCodec: Realtek ALC1220
Codec: Intel Kabylake HDMI

---

