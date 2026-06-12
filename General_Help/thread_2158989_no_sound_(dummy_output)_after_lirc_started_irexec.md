---
title: "no sound (dummy output) after lirc started irexec"
date: 2013-07-01
forum: General Help
---

### Post by lodhuang on 2013-07-01
Dear all,

Thanks for your time to undertand my problem.

Recently I started irexec (by /etc/init.d/lirc) for remote to start programs.
However, it's found no sound output. In the gnome sound setting, the sound output device became "dummy output".
I tried to kill irexec by "sudo killall irexec", the sound was back again and showed a "built-in audio analog stereo" output device.
lsmod showed "snd_hda_intel" module is correctly loaded (for a ALC1200 sound device).

In a boot flow without starting irexec, the sound functions normally. 
The problem seems to only happens when starting irexec in boot flow.
(sound is normal starting irexec after normal boot)

Googled but no solid solution was found.
Has anyone one suffered similar problem ?
Thanks in advance for your suggestion.


lod.huang

---

### Post by lodhuang on 2013-07-03
sorry, forgot to say, my ubuntu is 12.04 LTS 32-bit version.

---

