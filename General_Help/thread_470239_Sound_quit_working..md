---
title: "Sound quit working."
date: 2007-06-10
forum: General Help
---

### Post by icefloe on 2007-06-10
I've looked at several of the posts about sound not working and none seem to really apply to me.  I have an Asus Striker Extreme with the sound card that comes with it.  Sounds were working just fine until earlier today when I frelled my sudo ability.  I got that fixed in recovery mode through the command line thanks to forum staff aysiu that had a post pointing to the psychocats page.  Now, everything works like it should (as far as I can tell) except for sound.  The little speaker icon on the panel has the little slash symbol on it.  Double clicking it gives me this message:

No volume control GStreamer plugins and/or devices found.

Yet according to Synaptic I have quite a few GStreamer things installed.  I even marked them for re-install with no joy.  What simple thing am I missing that I messed up when I accidently messed up my sudo privileges?

Thanks...

---

### Post by icefloe on 2007-06-11
Okay, I tried running volume monitor and it said "Cannot connect to sound daemon.  Please run 'esd' at a command prompt."  So I did and this is the output I received from esd:

ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default

What in the world have I done to my Feisty Fawn?  LOL  On another note, I first tried to run esd from "Terminal Program - Super User Mode".  I heard a series a beeps go up in pitch and then nothing in the window.  I closed it and then ran it from a regular konsole.  Oops.   LOL

**edit**  Had to turn off smilies

---

