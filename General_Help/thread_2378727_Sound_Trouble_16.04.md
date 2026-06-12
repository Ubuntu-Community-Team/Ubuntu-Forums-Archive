---
title: "Sound Trouble 16.04"
date: 2017-11-26
forum: General Help
---

### Post by scherzkeks on 2017-11-26
Hey,

i wanted to give ubuntu 16.04 a try but my sound doesn't work.

In the sound menu no output device is listed, but as far as i can tell my PC detects the sound card. I tried to solve my problem via Google but so far nothing worked.
Since i'm new i have no idea what to look out for so please tell me if you need more information. Here we go.


[B] aplay -l
[/B]
**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: HDMI [HDA Intel HDMI], Gerät 3: HDMI 0 [HDMI 0]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0

[B]cat /proc/asound/cards
[/B]
 0 [HDMI           ]: HDA-Intel - HDA Intel HDMI
                      HDA Intel HDMI at 0xf7a18000 irq 50

[B]lspci -v
[/B]
Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
    Subsystem: ASUSTeK Computer Inc. Haswell-ULT HD Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 49
    Memory at f7a18000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

**aplay /usr/share/sounds/alsa/Front_Center.wav**
Wiedergabe: WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate: 48000 Hz, mono


When i play a yt video, pavucontrol shows that sound is played despite i don't hear anything, 

Also Alsamixer doesn't show any bars 

So yeah, pls help :D also let me know if you need more information.

Thanks

---

### Post by Yellow Pasque on 2017-11-26
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by scherzkeks on 2017-11-26
Here you go
[http://www.alsa-project.org/db/?f=89818522afb6f4bcef4c7d9a2bf0e2eab71151c0](http://www.alsa-project.org/db/?f=89818522afb6f4bcef4c7d9a2bf0e2eab71151c0)


thanks in advance

---

### Post by Yellow Pasque on 2017-11-26
Only an HDMI sound device shows up. Is that what you're trying to use (i.e. sound through video cable to a display with speakers)?

I would check the BIOS to see if there is a setting to enable/disable the audio codec. Perhaps you can reset the BIOS to defaults? 
lspci output should show an additional audio device named something like:
```
Audio device: Intel Corporation 8 Series HD Audio Controller
```

---

### Post by scherzkeks on 2017-11-28
No, just trying to use my laptop speakers. External Speakers don't work either. 
On my TV via HDMI the sound works. (i just noticed, didn't think of it earlier sry)

Checked the BIOS and restored the default but with no success.

**lspci:**
**00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)**
00:04.0 Signal processing controller: Intel Corporation Device 0a03 (rev 0b)
00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series HECI #0 (rev 04)
[B]00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)


[/B]thanks

---

### Post by Yellow Pasque on 2017-11-28
The device now shows up in lspci. That is significant progress. You should be able to select it and use it. If you can't, please run the alsa info script again.

---

