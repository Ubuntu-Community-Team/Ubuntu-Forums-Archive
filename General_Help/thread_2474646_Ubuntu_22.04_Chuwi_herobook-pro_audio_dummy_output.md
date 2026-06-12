---
title: "Ubuntu 22.04 Chuwi herobook-pro audio dummy output"
date: 2022-05-04
forum: General Help
---

### Post by caplico on 2022-05-04
Hello, as the title suggests, I have a chuwi herobook pro with dual boot windows and ubuntu 22 installed. 
My problem is that with ubuntu the sound does not work while if I start windows it works regularly. 
I have tried to follow a lot of guides but with no results.
Below I leave the result of aplay -l and inxi -Axx 
Thanks
```
   
 aplay -l
**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: sofhdadsp [sof-hda-dsp], dispositivo 1: HDMI1 (*) []
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: sofhdadsp [sof-hda-dsp], dispositivo 2: HDMI2 (*) []
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: sofhdadsp [sof-hda-dsp], dispositivo 3: HDMI3 (*) []
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
   
```

```
 
   inxi -Axx
Audio:
  Device-1: Intel Celeron/Pentium Silver Processor High
    Definition Audio
    driver: sof-audio-pci-intel-apl bus-ID: 00:0e.0
    chip-ID: 8086:3198
  Sound Server-1: ALSA v: k5.15.0-27-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
     
```

---

