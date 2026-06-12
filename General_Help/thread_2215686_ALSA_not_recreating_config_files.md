---
title: "ALSA not recreating config files"
date: 2014-04-07
forum: General Help
---

### Post by dylan16 on 2014-04-07
I previously installed jackd, and then tried to unisntall it.  But then alsa kept complaining about some jackd plugin, so I went and deleted the alsa config folder.  Well now I realize that there is no way to get back the alsa.conf file and now whenever I run Skype I keep getting this error message:

ALSA lib conf.c:3707:(snd_config_update_r) Cannot access file /usr/share/alsa/alsa.conf
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM default

Does anyone know how to get back the config files? I have already tried reinstalling everything multiple times, but the alsa.conf file never comes back.

---

### Post by ian-weisser on 2014-04-09
```
$ dpkg -S /usr/share/alsa/alsa.conf
libasound2-data: /usr/share/alsa/alsa.conf
```

Try reinstalling libasound2-data instead of alsa.

---

### Post by dylan16 on 2014-04-26
Thanks! That fixed the problem.

---

