---
title: "Sound error in wine and warcraft3"
date: 2006-08-06
forum: General Help
---

### Post by Namtellum on 2006-08-06
Hi there, I'm fairly new to ubuntu and very new to wine. I finally have warcraft3 running at a good framerate but I'm not getting any sound. When I run winecfg i get this error```
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack

```
I do however get perfect sound on the splash screen to start warcraft. Also a side problem, after closing warcraft my resolution changes from 1280x1024 down to 1024x768 every time. Thanks in advance for any help.

---

### Post by Namtellum on 2006-08-07
bump. still can't figure this out.

---

### Post by nischirat on 2006-08-07
as root do: modprobe snd_seq

---

