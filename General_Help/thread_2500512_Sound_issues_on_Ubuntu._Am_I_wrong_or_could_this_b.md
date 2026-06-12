---
title: "Sound issues on Ubuntu. Am I wrong or could this be the problem."
date: 2024-09-04
forum: General Help
---

### Post by falloutboy2 on 2024-09-04
At the moment on my server which has no sound system of its own I have a C-Media 8828 Sound card and an nVidia 4060Ti when I have headphones attached to the C-Media card I get clicks and pops but no other Audio and my thought is that maybe the HDMI Audio outputs on the 4060Ti may have been assigned as the primary Audio Out..

I have no way of testing this? can anyone suggest a way?

BTW My monitor has no speakers. So HDMI Audio out is pretty useless.

---

### Post by Holger_Gehrke on 2024-09-04
```

aplay --list-devices

```
will show you what sound hardware the Kernel (or the ALSA modules in the kernel) sees.
```

pactl info

```
should show you the default sink for PulseAudio (the sound server mostly still in use; in the long run it's probably going to be replaced by pipewire but I don't know any simply way to ask for similar information from that set of tools)

Holger

---

### Post by falloutboy2 on 2024-09-04
O.K so for the first command this was returned..

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMedia [HDA C-Media], device 0: Generic Analog [Generic Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMedia [HDA C-Media], device 1: Generic Digital [Generic Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Initially the second command kicked up an error asking for pactl to be installed, it wasn't installed despite having the nVidia card as an audio endpoint as well as the C Media card when UBuntu was installed.. so I installed that and running it returns..

Server String: /run/user/1000/pulse/native
Library Protocol Version: 35
Server Protocol Version: 35
Is Local: yes
Client Index: 99
Tile Size: 65472
User Name: <MyName>
Host Name: Primary-Server
Server Name: PulseAudio (on PipeWire 1.0.5)
Server Version: 15.0.0
Default Sample Specification: float32le 2ch 48000Hz
Default Channel Map: front-left,front-right
Default Sink: alsa_output.pci-0000_41_00.0.analog-stereo
Default Source: alsa_input.pci-0000_41_00.0.analog-stereo
Cookie: e2cd:b411

I did an ```
 lspci -vv | grep 41:00.0
``` and it returns this..
41:00.0 Audio device: C-Media Electronics Inc CM8888 [Oxygen Express]

---

### Post by Yellow Pasque on 2024-09-05
I'm doubting the HDMI is the problem, but if you want to disable it, see: [https://forums.linuxmint.com/viewtopic.php?t=340094](https://forums.linuxmint.com/viewtopic.php?t=340094)
In your setup, it looks like you would want enable=0,1

> **Holger_Gehrke said:**
> I don't know any simply way to ask for similar information from that set of tools

```
wpctl status
```

---

