---
title: "Sound card trouble - No sound!"
date: 2007-11-20
forum: General Help
---

### Post by AxAeo on 2007-11-20
While I was out my brother tried running my media player on Windows on my PC and called me to tell me that the sound wasn't working... When I got home and tried in Ubuntu i did some tests and determined that the sound card was having a problem. Later I restarted my computer to get some choppy sound with a couple of glitches. (Eventually my computer froze). After that I opened up the box and checked the PCI connections and made sure it was inserted fully. Now I have restarted my computer and the sound card is detected and works as far as I know... Except I'm not getting any sound whatsoever, on Windows or Ubuntu. Can anybody lend me a hand here?

---

### Post by reckless2k2 on 2007-11-20
well if it's not working in both, i'd suggest going to the store and getting a new one. either that or maybe sit on santa's lap at the mall and ask for it nicely. if you're on the good list you should be fine.

---

### Post by AxAeo on 2007-11-20
The command 

```
aplay -l
```

returns this

> **** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [Audigy 4 [SB0610]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy2 [Audigy 4 [SB0610]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [Audigy 4 [SB0610]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Is my soundcard shot? :(

---

