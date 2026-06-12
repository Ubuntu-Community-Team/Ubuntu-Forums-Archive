---
title: "modprobe"
date: 2006-11-11
forum: General Help
---

### Post by shinythings on 2006-11-11
I screwed up my sound by tinkering (trying to get my headphones to work) and have been following [http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449) to try and fix it. Everything seems to work fine until I try

```
sudo modprobe snd-hda-intel
```

at which point *nothing* happens. The console simply sits there. I have no idea what the problem is. I have compiled the driver from alsa-source (no errors).

On a side-note, sound worked fine (except for the headphone problem) when I first installed Edgy.
```

lspci -v 

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1173
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at febf8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

```

```
aplay -l
aplay: device_list:222: no soundcards found...

```

```
modprobe -l snd*
/lib/modules/2.6.17-10-generic/kernel/sound/acore/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.17-10-generic/kernel/sound/acore/seq/snd-seq.ko
/lib/modules/2.6.17-10-generic/kernel/sound/acore/seq/snd-seq-midi-event.ko
/lib/modules/2.6.17-10-generic/kernel/sound/acore/seq/snd-seq-device.ko
/lib/modules/2.6.17-10-generic/kernel/sound/acore/oss/snd-pcm-oss.ko
/lib/modules/2.6.17-10-generic/kernel/sound/acore/oss/snd-mixer-oss.ko
/lib/modules/2.6.17-10-generic/kernel/sound/acore/snd.ko
/lib/modules/2.6.17-10-generic/kernel/sound/acore/snd-timer.ko
/lib/modules/2.6.17-10-generic/kernel/sound/acore/snd-rtctimer.ko
/lib/modules/2.6.17-10-generic/kernel/sound/acore/snd-pcm.ko
/lib/modules/2.6.17-10-generic/kernel/sound/acore/snd-page-alloc.ko
/lib/modules/2.6.17-10-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.17-10-generic/kernel/sound/pci/hda/snd-hda-codec.ko
```

Any ideas?

---

### Post by shinythings on 2006-11-11
Hmmm, I get the feeling I have broken something

```
lsmod | grep snd
snd_timer              27529  1 
snd                    66924  1 snd_timer
soundcore              11232  1 snd
```

Surely there should be a lot more there?!

---

### Post by .t. on 2006-11-11
Yeah: I have all this:```
snd_intel8x0           34844  3 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  2 
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          19584  1 snd_pcm_oss
snd_seq_dummy           4996  0 
snd_seq_oss            36480  0 
snd_seq_midi            9984  0 
snd_rawmidi            27264  1 snd_seq_midi
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
snd_seq                59120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              25348  2 snd_pcm,snd_seq
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    58372  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              11232  3 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
```

Why are you building the drivers anyway?

---

### Post by shinythings on 2006-11-11
Thanks for that. Now I just need to figure out how to get all the necessary modules back I guess :D

Am building the drivers because I am desperate! For some reason my sound card is no longer automatically recognised, although it was when I initially installed Edgy. Short of reinstalling everything it was the only thing I could think of. (I have been trying everything suggested in [http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449) )

Is there a way to completely 'reset' everything sound-related and get it to do the same thing it would on clean install?

---

### Post by .t. on 2006-11-11
Well, try uninstalling the stuff you've tried building, for starters.

---

### Post by shinythings on 2006-11-12
I've managed to fix it. I think I broke it in the first place by removing *too much* after trying to get rid of my botched install.](*,)  

After seeing how many modules were missing I uninstalled (purged) the kernel and reinstalled it and now everything seems be running smoothly. Thanks for your help!

---

### Post by .t. on 2006-11-12
Well; no problem, I guess... I didn't really do much...

---

### Post by michalg on 2006-11-12
> **.t. said:**
> Yeah: I have all this:```
snd_intel8x0           34844  3 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  2 
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          19584  1 snd_pcm_oss
snd_seq_dummy           4996  0 
snd_seq_oss            36480  0 
snd_seq_midi            9984  0 
snd_rawmidi            27264  1 snd_seq_midi
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
snd_seq                59120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              25348  2 snd_pcm,snd_seq
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    58372  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              11232  3 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
```

Why are you building the drivers anyway?

i also followed the comprehensive sound guide, and followed the "failure" path until i compiled the alsa drivers from source manually. after issuing many modprobe commands, i have this as my output of lsmod | grep snd, with items missing from your list inserted by me:

```

snd_hda_intel          20500  0
snd_hda_codec         169088  1 snd_hda_intel
(no snd_intel8x0)
(no snd_ac97_codec)
(no snd_ac97_bus)
snd_pcm_oss            47232  0
snd_pcm                84612  3 snd_pcm_oss,snd_hda_intel,snd_hda_codec
snd_mixer_oss          19712  1 snd_pcm_oss
(no snd_seq_dummy)
snd_seq_oss            38272  0
(no snd_seq_midid)
(no snd_rawmidi)
snd_seq_midi_event      8960  1 snd_seq_oss
snd_seq                59888  4 snd_seq_oss,snd_seq_midi_event
snd_timer              24964  2 snd_seq,snd_pcm
snd_seq_device          9868  2 snd_seq_oss,snd_seq
snd                    60036  9 snd_seq_oss,snd_seq,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_hda_intel,snd_hda_codec,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11656  2 snd_hda_intel,snd_pcm

```

yet aplay -l still reports that there is no soundcard. basically i've started getting a similar problem to the OP, and reported it at [http://ubuntuforums.org/showthread.php?p=1747152](http://ubuntuforums.org/showthread.php?p=1747152).

oh, and when i "modprobe -v hda-intel", dmesg reports:

> 
[17181068.900000] ALSA /moo/mikeg/tmp/sound-problem/src/alsa/alsa-driver-1.0.12/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1554: hda-intel: no codecs found!


and now i'm stuck.

-Michal

---

### Post by .t. on 2006-11-12
The only modules you are "missing" are ones specific to my sound card. If I had my other in, it would be more different still.

Was it necessary to compile the modules yourself? Have you tried again as above with the standard kernel? I'll post in your thread.

---

