---
title: "Strange ALSA errors"
date: 2006-11-09
forum: General Help
---

### Post by buzst on 2006-11-09
I suspect something is wrong but don't know what or what to do about it.

When I open a terminal window then type sudo "whatever" as follows:


buz@office2:~$ sudo gedit
Password:

ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card 'default'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default


The above error messages are displaed in the window then the sudo operation is performed. Can anyone tell me whats going on and what I should do?

Thanks in advance
buz

---

