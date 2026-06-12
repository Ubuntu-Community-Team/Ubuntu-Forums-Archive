---
title: "Sound not working in Ubuntu Server 13.04"
date: 2013-05-06
forum: General Help
---

### Post by Zukaro on 2013-05-06
I'm trying to get audio to work on Ubuntu Server 13.04 as I want to use it as an alarm clock (I had an old PC lying around doing nothing so I wanted to use it to make my own alarm clock and maybe add some other stuff eventually as well).
I installed ALSA and when I try testing the speakers I get the following errors:

```
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4720:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:682: audio open error: No such file or directory

```

I'm not sure how to resolve the issue.  I've gone into alsamixer and unmuted everything as well.

---

