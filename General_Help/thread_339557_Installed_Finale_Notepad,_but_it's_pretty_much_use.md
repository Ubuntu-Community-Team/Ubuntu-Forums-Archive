---
title: "Installed Finale Notepad, but it's pretty much useless"
date: 2007-01-15
forum: General Help
---

### Post by k1001001 on 2007-01-15
I used wine to install Finale Notepad. It's up and running, which is a first for me trying to install a program using wine. However, you can't select what note value you want, the system responses are slow, and playback is very choppy. It's pretty much useless at this point.

Something that might help:
When I run winecfg, and go to the Audio tab, I get this error message:
```
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card 'default'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
```
So I try running JACK, but this doesn't seem to help.

Any ideas as to what the problem could be?

---

### Post by Master Grah on 2008-05-20
Hey, it's further than I got; I don't even get sound.

---

### Post by basta638 on 2008-06-07
At my computer finale works fine, but I don't get any sound during playback.

---

