---
title: "LTSP client skype freeze"
date: 2008-07-09
forum: General Help
---

### Post by sgk_ on 2008-07-09
Hi Guys
Something weird is happening with my ltsp clients and the server. I've setup ltsp ubuntu 8.04 server, everything works fine, except skype. When i try to turn it off, then sometimes the client is freezing, sometimes not, but in any case after quiting skype the server cpu goes 98-99% of usage, and whole system is slowing down, normally...
The kernel cannot kill that process.

Any ideas, what can cause these...?

Thanks in help and advice!


Dell PowerEdge200 Xeon cpu,4GBram, Ubuntu 8.04 LTS (alternate) LTSP server
2.6.24-19-generic SMP kernel


here's the skype debug

ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM dsnoop

---

