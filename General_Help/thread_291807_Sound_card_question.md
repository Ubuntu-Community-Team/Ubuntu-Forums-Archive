---
title: "Sound card question"
date: 2006-11-03
forum: General Help
---

### Post by Cable on 2006-11-03
This thread directly relates to [this one]("http://www.ubuntuforums.org/showthread.php?t=290977") posted by yours truly.  I created this thread as I felt it necessary to make one that was more direct, detailed, and seemingly more related to the actual problem than its symptoms.

Is there a way to either...

1)  Completely disable a soundcard?  I've disabled my onboard soundcard via the BIOS, and it is still showing up in Linux.  I only want my Audigy 2 to show up, as it's causing the issue in the thread linked to above.

or

2)  Change which sound card shows up as 0 and which shows up as 1?  To elaborate, when I do
```

aplay --list-devices

```My onboard card is showing up as card 0, and my Audigy 2 is showing as card 1.  Here is the output...
```

**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 2 [SB0240]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 1: Audigy2 [Audigy 2 [SB0240]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Audigy2 [Audigy 2 [SB0240]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 2 [SB0240]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``` I have a suspicion that if I was able to change my Audigy 2 to card 0, that I wouldn't be having the problem linked to above.

I would ***REALLY ***appreciate help here.  Thanks a lot to anyone who knows how to fix this

---

### Post by woedend on 2006-11-03
yes, see [http://www.ubuntuforums.org/showthread.php?t=291451](http://www.ubuntuforums.org/showthread.php?t=291451)

---

