---
title: "AC97: Static When Playing Sounds Problem"
date: 2006-12-03
forum: General Help
---

### Post by pzaully on 2006-12-03
howdy,

I've been having some trouble with my sound, initially I was using kubuntu and thought it might be a problem with aRts, however I now have ubuntu installed with gnome and the problem is persisting. Whenever sound is played theres a bunch of static with it. I've tried completely removing and reinstalling alsa along with making sure I was using the correct modules without any luck. Heres a bit of info

```

paul@peanuts:~$ lsmod | grep snd
snd_intel8x0           34844  1 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm


```

```

paul@peanuts:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

lspci -v
```

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: Unknown device 1919:1005
        Flags: bus master, medium devsel, latency 0, IRQ 201
        I/O ports at d800 [size=256]
        I/O ports at dc00 [size=64]
        Memory at febff800 (32-bit, non-prefetchable) [size=512]
        Memory at febff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2


```

Any help would be appreciated, the static is rather annoying. 
Thanks,
pzaully

---

### Post by pzaully on 2006-12-03
Looks like all it needed was to be rebooted. Possibly during the setup of the installation, on the first boot, something was running that was causing problems.

---

