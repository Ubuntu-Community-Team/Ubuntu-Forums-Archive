---
title: "Sound Error"
date: 2007-09-11
forum: General Help
---

### Post by Roarden on 2007-09-11
Hi all,

Sound had been working before in the past week (for the most part.. couldn't get microphone to work), and suddenly today, I'm getting all these random errors and no sound.

Whenever I'm working in the terminal and save something with gedit or the like this pops up:
```
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave

```

And additionally, whenever I test ANY sound options in gnome's sound config, I get this:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Resource busy or not available.
```

For reference I have two sound cards.  If it helps, here is my aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


Any suggestions are appreciated

---

### Post by amanjsingh on 2007-09-12
> **Roarden said:**
> Hi all,


And additionally, whenever I test ANY sound options in gnome's sound config, I get this:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Resource busy or not available.
```


i am facing the same error. My sounds were working fine before yesterday and I am sure all I did was a regular automatic update from Ubuntu servers.

Thanks.
AJ

---

### Post by amanjsingh on 2007-09-13
> **Roarden said:**
> Hi all,

Sound had been working before in the past week (for the most part.. couldn't get microphone to work), and suddenly today, I'm getting all these random errors and no sound.

Whenever I'm working in the terminal and save something with gedit or the like this pops up:
```
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave

```

And additionally, whenever I test ANY sound options in gnome's sound config, I get this:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Resource busy or not available.
```



Any suggestions are appreciated

Hi Roarden,

I configured mine successfully. You must re-install your ALSA drivers and here is the article you need - [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Enjoy.

Amanjeev

---

