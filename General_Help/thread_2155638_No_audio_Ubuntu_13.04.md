---
title: "No audio Ubuntu 13.04"
date: 2013-06-18
forum: General Help
---

### Post by jhaykage on 2013-06-18
Issue: No sound comes from built-in speakers and headphone jacks after doing a clean install of Ubuntu 13.04

Setup: Dual-boot with Windows Vista Home Basic (used mainly for Adobe CS)
Audio: Intel HDA
Chip: Conexant CX20561 (Hermosa)

Here's what I get when I run ```
aplay -l
``` in Terminal:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I've already updated the alsa and pulseaudio drivers after the clean install, still no sound.

Caveat: No sound as well when logged into Windows Vista partition even if sound card/device is listed as installed and working properly in Device Manager. Audio driver and BIOS has already been updated as an attempt to fix the issue.

Help!

---

### Post by CatKiller on 2013-06-19
Maybe it just doesn't work?

It's probably muted somewhere.

---

### Post by Daktyl198 on 2013-06-19
I've had issues with my S/PDIF audio not working before. I fixed it by looking in alsamixer and finding out that the main channel was muted.

Maybe the channel you are trying to use is muted. Just open a terminal and type ```
alsamixer
```

---

### Post by jhaykage on 2013-06-19
> **Daktyl198 said:**
> I've had issues with my S/PDIF audio not working before. I fixed it by looking in alsamixer and finding out that the main channel was muted.

Maybe the channel you are trying to use is muted. Just open a terminal and type ```
alsamixer
```

Here's what my alsamixer looks like after bootup, S/PDIF is muted by default.

[IMG]http://farm8.staticflickr.com/7382/9084640688_78f07305da.jpg[/IMG]

I tried to unmute it but I still get no sound.

---

### Post by mafi127 on 2013-07-17
Got the same card, and dont have sound also.

---

