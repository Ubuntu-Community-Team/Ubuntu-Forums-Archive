---
title: "Ubuntu+X-Fi+DOSBox=i cannot hear the badguys die"
date: 2008-05-12
forum: General Help
---

### Post by AmishFury on 2008-05-12
i cannot get sound to work in dosbox at all... i get these errors

```
DOSBox version 0.72
Copyright 2002-2007 DOSBox Team, published under GNU GPL.
---
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
CONFIG: Using default settings. Create a configfile to change them
MIXER:Can't open audio: No available audio device , running in nosound mode.
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
ALSA:Can't open sequencer
MIDI:Opened device:none
```

now because the X-Fi drivers from creative refuse to install i have to use OSS4 to get sound working so all these ALSA errors are explained... so the question is how do i get sound working?

---

