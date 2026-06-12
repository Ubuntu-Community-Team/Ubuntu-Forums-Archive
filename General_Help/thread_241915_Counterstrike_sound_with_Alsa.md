---
title: "Counterstrike sound with Alsa"
date: 2006-08-23
forum: General Help
---

### Post by maka on 2006-08-23
In winecfg,
under the audio tab
when i select OSS for sound, i experience no problem with cs except that I wont be able to play music or hear sounds in the background except CS.

when I select ALSA for sound, CS hangs when it is loading and doesnt load.

with ALSA selected, when I open winecfg and go to the audio tab
i have these errors show up in the terminal:

```
~$ winecfg
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
```

---

### Post by encompass on 2006-08-23
It talks of "Jack" when I look for Librarys in synaptic with jack I got some interesting results... you could try installing one of those..
libjack0.100 is my best bet... not the devs but the first one when you search by name for libjack
Tell me if it fixes it cool... if it doesn't save some space and remove it.
I am guessing.

---

