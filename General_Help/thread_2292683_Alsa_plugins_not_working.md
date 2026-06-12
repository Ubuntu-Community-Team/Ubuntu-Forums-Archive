---
title: "Alsa plugins not working"
date: 2015-08-30
forum: General Help
---

### Post by maxionix on 2015-08-30
Hello. I've been trying to achieve a similar sound effect to dolby heapdhones under Linux, and I've found that the best option would be to use system wide audio plugins.
I have the tap-plugins installed, then aplay -l gives me
```

card 0: DX [Xonar DX], device 0: Multichannel [Multichannel]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: DX [Xonar DX], device 1: Digital [Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 11: HDMI 5 [HDMI 5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



```
I obviously want the analog xonar device, so I create a /etc/asound.conf file with sudo gedit and then I put the following code:[COLOR=#000000][FONT=Times New Roman]
[/FONT][/COLOR]```
pcm.!default {
 type plug
 slave.pcm "headphones"
}


pcm.headphonesplug {
 type plug
 slave.pcm "headphonesduplex"
}
pcm.headphonesduplex {
 type asym
 capture.pcm "hw:0,0"
 playback.pcm "hw:0,0"
}


pcm.bs2b {
 type ladspa
 slave.pcm "headphonesplug"
 path "/usr/lib/ladspa"
 plugins [
  {
   label tap_bs2b
   input {
    controls [ 3 1 ]
   }
  }
 ]
}


pcm.headphones {
 type plug
 slave {
  pcm "bs2b"
  rate 44100
 }
}

```
The problem is, it doesn't work. Nothing is happening. I've found similar configurations on various websites and nothing has any effect whatsoever. I feel like I'm missing something fundamental from the configuration process.

---

### Post by dino99 on 2015-08-30
ubuntu use pulseaudio, but is very sensitive about:
- jacks have to be well plugged (same color)
- bios/uefi set on hda not ac97

then install paref & pavucontrol to fine tune your needs from the Sound -> Pulseaudio Volume Control menu (check the 2 tabs)

---

### Post by maxionix on 2015-08-30
> **dino99 said:**
> ubuntu use pulseaudio, but is very sensitive about:
- jacks have to be well plugged (same color)
- bios/uefi set on hda not ac97

then install paref & pavucontrol to fine tune your needs from the Sound -> Pulseaudio Volume Control menu (check the 2 tabs)
What is paref and how does that help me get virtual surround sound ?

---

