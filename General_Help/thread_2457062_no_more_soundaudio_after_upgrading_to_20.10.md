---
title: "no more sound/audio after upgrading to 20.10"
date: 2021-01-25
forum: General Help
---

### Post by alain.roger on 2021-01-25
Hi,

after upgrading to ubntu 20.10 I lost audio/sound on my computer. Till then it was working greate even if 1 or 2 days after upgrade.
I remove alsa drivers and i reinstall them but without any result.

if i type "aplay --version" result is: v 1.2.3

aplay -l command returns:
```
[FONT=monospace][COLOR=#000000]**** List of PLAYBACK Hardware Devices ****[/COLOR]
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 11: HDMI 5 [HDMI 5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 12: HDMI 6 [HDMI 6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/FONT]
```

so basically the first device should be used. However i even do not have the sound/speaker icon in my taskbar (i user KDE 5.20).

alsamixer returns:
[[IMG]https://i.ibb.co/hctxkPn/2021-01-25-alsamixer-sound-issue.png[/IMG]]("https://ibb.co/PMfsR7b")

[FONT=monospace][COLOR=#000000]if i type: inxi -SMA
[/COLOR]System returns:

```
[COLOR=#5454FF]**System:    Host:**[/COLOR][COLOR=#000000] PC0001 [/COLOR][COLOR=#5454FF]**Kernel:**[/COLOR][COLOR=#000000] 5.10.0-051000-generic x86_64 [/COLOR][COLOR=#5454FF]**bits:**[/COLOR][COLOR=#000000] 64 [/COLOR][COLOR=#5454FF]**Desktop:**[/COLOR][COLOR=#000000] KDE Plasma 5.19.5  [/COLOR]
           [COLOR=#5454FF]**Distro:**[/COLOR][COLOR=#000000] Ubuntu 20.10 (Groovy Gorilla)  [/COLOR]
[COLOR=#5454FF]**Machine:   Type:**[/COLOR][COLOR=#000000] Desktop [/COLOR][COLOR=#5454FF]**Mobo:**[/COLOR][COLOR=#000000] ASUSTeK [/COLOR][COLOR=#5454FF]**model:**[/COLOR][COLOR=#000000] P8Z77-V [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] Rev 1.xx [/COLOR][COLOR=#5454FF]**serial:**[/COLOR][COLOR=#000000] <superuser/root required> [/COLOR][COLOR=#5454FF]**BIOS:**[/COLOR][COLOR=#000000] American Megatrends  [/COLOR]
           [COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] 2104 [/COLOR][COLOR=#5454FF]**date:**[/COLOR][COLOR=#000000] 08/13/2013  [/COLOR]
[COLOR=#5454FF]**Audio:     Device-1:**[/COLOR][COLOR=#000000] Intel 7 Series/C216 Family High Definition Audio [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] snd_hda_intel  [/COLOR]
           [COLOR=#5454FF]**Device-2:**[/COLOR][COLOR=#000000] NVIDIA TU106 High Definition Audio [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] snd_hda_intel  [/COLOR]
           [COLOR=#5454FF]**Device-3:**[/COLOR][COLOR=#000000] Creative Live! Cam Connect HD 1080 VF0760 [/COLOR][COLOR=#5454FF]**type:**[/COLOR][COLOR=#000000] USB [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] snd-usb-audio,uvcvideo  [/COLOR]
           [COLOR=#5454FF]**Sound Server:**[/COLOR][COLOR=#000000] ALSA [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] k5.10.0-051000-generic [/COLOR]
```

[/FONT]so i do not understand where is the issue.

the result is the same if I use kernel 5.10, 5.9 or 5.8

Any idea what should I check/test ?

thx

---

### Post by alain.roger on 2021-01-25
for an unknown reason i had to reinstall plasma-pa package like:
```
sudo apt install plasma-pa
```

after that i select my audio output and it works ... weird.

---

