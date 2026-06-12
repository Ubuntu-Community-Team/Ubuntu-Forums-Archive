---
title: "How to fix volume control in 16.04-17.10?"
date: 2017-10-27
forum: General Help
---

### Post by mikewhatever on 2017-10-27
Greetings, I use an old HP5000 notebook, which has been working quite well with Ubuntu since about 2008. In particular, sound and volume controls worked out of the box in 8.04 through 14.04, but with the newer releases there are regressions. 

[LIST]
[*]Moving the volume slider in the top panel doesn't change volume levels.
[*]
[*]Moving the Master channel up or down in alsamixer doesn't change volume levels.
[*]
[*]PCM is the only channel in alsamixer that affects volume levels.
[*]
[*]There is static noise in the speakers/headphones.
[/LIST]

I've been trying workarounds like [volume = ignore]("https://askubuntu.com/questions/32383/adjust-pcm-volume") and [ignore_dB=1]("https://askubuntu.com/questions/15069/how-do-i-change-the-way-ubuntu-adjusts-my-volume-mixer-levels") and [bdl_pos_adj]("https://unix.stackexchange.com/questions/203792/bdl-pos-adj-set-irq-timing-workaround-for-hda-intel") and various "model=..." option, none of which helped. Reinstalling alsa-base and pulseaudio, or reloading modules also had no effect.

For comparison, here are the outputs of alsa-info from 14.04 and 17.04: [alsa-info-14.04]("https://paste.ubuntu.com/25832088/") and [alsa-info-17.04]("https://paste.ubuntu.com/25832096/").

Anyone knows how to fix it? If you need more info, please ask.

---

