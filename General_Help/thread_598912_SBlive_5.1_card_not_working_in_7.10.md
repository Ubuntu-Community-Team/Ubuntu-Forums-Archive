---
title: "SBlive 5.1 card not working in 7.10"
date: 2007-10-31
forum: General Help
---

### Post by Mike7171 on 2007-10-31
I just updated, and now I have no sound. This has happened before when I first started using Ubuntu. I fixed it, but I forgot how. Anyone know how to solve this?

Results of "aplay -l" if it helps:
> **** List of PLAYBACK Hardware Devices ****
card 0: rev50 [VIA 82C686A/B rev50], device 0: VIA 82C686A/B rev50 [VIA 82C686A/B rev50]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [SBLive 5.1 [SB0060]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 1: Live [SBLive 5.1 [SB0060]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Live [SBLive 5.1 [SB0060]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Mike7171 on 2007-10-31
I just tried changing between the options in the preferences part when I right-click on the speaker icon in the upper-right corner of the screen. Didn't help.

---

### Post by the yawner on 2007-10-31
Try *asoundconf set-default-card Live* on the terminal. (no sudo needed)

---

### Post by Mike7171 on 2007-10-31
That did not work either.

---

### Post by php on 2007-11-04
I have a similar problem... I have had mythfrontend configured to use "digital-hw" with custom .asoundrc to get both AC3 passthrough and standard stereo sound through the SPDIF output on the SBlive. After 7.10 only passthrough works, not standard stereo...

---

### Post by dantienn on 2007-11-08
I have the same problem with the same sound chip. i just installed kubuntu for first time and everything beside the sound worked fine. 
I have dual boot with winxp, but that will be history soon :p

here is what i get when i type aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: rev50 [VIA 82C686A/B rev50], device 0: VIA 82C686A/B rev50 [VIA 82C686A/B rev50]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I guess it must be a bug on this sound chip. To bad i dont have another sound card...

---

### Post by Shazaam on 2007-11-08
Open a terminal and input ..
```
alsamixer
```
 Look for anything that has MM at the bottom. If you find one hit your "m" key to unmute it. Scroll to the right, there are a lot of things in there. Unmuted looks like "00"

---

### Post by dantienn on 2007-11-08
Thanks for the tip Shazaam. I already checked that. Sadly it wasnt that simple to fix :P
I have already started a new thread on this here: [http://ubuntuforums.org/showthread.php?p=3734451#post3734451](http://ubuntuforums.org/showthread.php?p=3734451#post3734451)
When i saw Mike7171 post i just wanted to say that he is not alone... :)

---

