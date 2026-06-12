---
title: "AC97 sound problem in Dapper Drake"
date: 2006-09-12
forum: General Help
---

### Post by tammx on 2006-09-12
Hi!
Last night I upgraded from Breezy Badger to Dapper Drake and after that my soundcard stopped working :(

>lsmod | grep snd
snd_pcm_oss            46368  0
snd_pcm                78344  1 snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd_page_alloc         10120  1 snd_pcm
snd_mixer_oss          16128  1 snd_pcm_oss
snd                    48644  4 snd_pcm_oss,snd_pcm,snd_timer,snd_mixer_oss
soundcore               9184  1 snd

>lspci | grep audio
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

> /etc/init.d/alsa-utils start
 * Setting up ALSA...  * warning: 'alsactl restore' failed with error message 'alsactl: load_state:1236: No soundcards found...'...                                            

Further more, even ">cat /dev/dsp" returns "cat: /dev/dsp: No such device" . Xmms with OSS output doesn't work, neither with ALSA, neither does anything else... 
Any ideas?

---

### Post by xenfasa on 2006-10-04
I don't know if I have AC97 .. but my laptop sound stopped working when I upgraded too... to Dapper Drake.

No idea how to fix it at this point

---

### Post by alecjw on 2006-10-04
I have the exact same chip. It worked with dapper, but not edgy.

Edit: Got it working. Go to System>Preferneces>Sound and play around with drivers until you find one whihc works.

---

