---
title: "Audio device not switching in Sound Preferences"
date: 2017-07-24
forum: General Help
---

### Post by bswarm2 on 2017-07-24
My FiiO E10K USB-DAC was working fine until today. Switching from the Built-In Audio to the USB-DAC in the Sound Preferences has no effect in any application even though Test Speakers works. The only change was a kernel update yesterday, but switching to the older kernel in grub still has no effect. I can get it working in Audacious and VLC by going into the menus and choosing the device, but the volume can't be controlled from the panel icon. All other apps are not getting sound.

Ubuntu Mate 17.04 64bit Intel Pentium J2900

---

### Post by bswarm2 on 2017-08-06
Bump. Is there any way to reset pulseaudio without reinstalling the OS? I can not get the sound panel applet to switch audio globally, the only way to get audio is by going into each app and choosing a device in the menu. Even then, I can't control the volume with the panel applet.
```
aplay -l**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC3239 Analog [ALC3239 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audio [DigiHug USB Audio], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Audio [DigiHug USB Audio], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



```

---

