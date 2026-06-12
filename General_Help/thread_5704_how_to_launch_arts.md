---
title: "how to launch arts"
date: 2004-11-21
forum: General Help
---

### Post by Razvan on 2004-11-21
Hi All,

i installed arts, which I prefer over esd...now how do I lauch it? All my programms are silent when I tell them to use arts and i cant find it in /etc/init.d/arts or something.

thanks for halp in advance, Martin

---

### Post by Razvan on 2004-11-21
ok...i found out, that i can launch it with artsd

```

root@razvan:/home/udssr # artsd
ALSA lib pcm_hw.c:549:(snd_pcm_hw_start) SNDRV_PCM_IOCTL_START failed: Broken pipe
ALSA lib pcm_hw.c:549:(snd_pcm_hw_start) SNDRV_PCM_IOCTL_START failed: Broken pipe

```

and xmms says i shall set up my sound card :-(

---

