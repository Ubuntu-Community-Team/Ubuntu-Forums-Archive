---
title: "Hosed my sound"
date: 2006-09-06
forum: General Help
---

### Post by Solver on 2006-09-06
I've had my sound working on Dapper in the past. I downloaded OpenSound, installed it, that was also okay. Soon, my sound stopped working - might have been at the next boot. I've tried my best to fix the problem, but can't even really figure out why it's happening. Symptoms: no sound whatsoever, under Preferences->Sound, no sound cards show up. Trying to execute alsactl commands makes it say there are no soundcards.

For the record, the sound card definitely is working (okay in XP), and it's a standard onboard card which worked in Breezy and Dapper before. I do have linux-sound-base, lib32asound2, gstreamer-alsa and alsa-base packages all installed, plus a few others. Tried reinstalling through Synaptic, no result.

I'm running the 64-bit version, by the way, but it doesn't seem to be related to the issue. Help on diagnosing & fixing the problem will be very welcome (I'd rather not reinstall, if I can avoid it) :).

---

### Post by Solver on 2006-09-07
Bump in hopes for help :).

---

### Post by Solver on 2006-09-08
Still not having the best of luck. Here's what I got now, lspci -v shows my sound:

```

0000:02:01.0 0403: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
        Subsystem: ASRock Incorporation: Unknown device 0888
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at f3dfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [70] #10 [0091]
```

However, executing aplay gives:

```
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:544: audio open error: No such device
```

I also do not have /dev/dsp. I'm still very much lost as to why the soundcard, showing up well on lspci, would fail to be seen elsewhere.

---

