---
title: "speakers troubleshoot"
date: 2016-10-06
forum: General Help
---

### Post by Itai_Edri on 2016-10-06
I have installed Ubuntu 16.04.1 on my new computer. I am playing music from the internal laptop speakers and sound does come out. Plugging in the external speakers still output sound from the internal laptop speakers!
I have plugged in my phone to the external speakers and it works great.
I have followed [this]("https://help.ubuntu.com/community/SoundTroubleshooting") manual, but it didn't help (the basic troubleshooting step).
Here are some information, if you need anything else please tell me.
```
itai@Negev:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
Home directory not accessible: Permission denied
card 0: PCH [HDA Intel PCH], device 0: ALC256 Analog [ALC256 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


```
itai@Negev:~$ lspci -v | grep -A7 -i "audio"
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
    Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP HD Audio
    Flags: bus master, fast devsel, latency 32, IRQ 130
    Memory at dfc28000 (64-bit, non-prefetchable) [size=16K]
    Memory at dfc00000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_soc_skl
```

---

### Post by Geoffrey_Arndt on 2016-10-06
Sometimes installing pavucontrol (pulse audio mixer) can help resolve this - - (assuming you've already tried the standard sound settings gui to change the output device with no success).

---

### Post by Itai_Edri on 2016-10-07
pavucontrol display only the built in speakers

---

### Post by colmax on 2016-10-07
have you tried pluging headphones into the output you r using
See if they cut off laptop speakers
Cheers

---

### Post by Itai_Edri on 2016-10-07
Headphone also does not make a sound

---

### Post by Geoffrey_Arndt on 2016-10-09
Read this thread - - especially the last two messages.   Also, youtube has videos on editing the alsamixer (worth watching).
[URL="https://ubuntuforums.org/showthread.php?t=2279687"]
https://ubuntuforums.org/showthread.php?t=2279687[/URL]

---

### Post by Itai_Edri on 2016-10-13
Thanks!
Sound does come out now, but there is still a weird behaviour.
When I plug in the head phones (or the external speakers) sound come out from both the internal computer speakers and the external speakers (or headphones).

---

