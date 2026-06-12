---
title: "what has ALSA got to do with vim?"
date: 2007-05-27
forum: General Help
---

### Post by engine on 2007-05-27
... or even vice-versa?

As you'll see, all I was doing was editing a couple of files as root ... so, assuming ALSA to be something to do with sound, why the sudden message when I (successfully) save my files? It's not even as though I have any sort of sound-effects turned on!

```
ngn@nbox:~$ sudo gvim /opt/coldfusionmx7/bin/cfstat
Password:
- using device /dev/dsp2
- using device /dev/dsp2
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM /dev/dsp2
```

Curious ...

---

### Post by Mikey_MW on 2007-05-27
Well, you weren't touching any sound related files were you? I'm not familier with that directory...

---

