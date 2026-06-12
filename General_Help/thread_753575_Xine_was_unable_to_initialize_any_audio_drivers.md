---
title: "Xine was unable to initialize any audio drivers?"
date: 2008-04-12
forum: General Help
---

### Post by N3um0rin on 2008-04-12
I don't know what happened..I restarted my computer RIGHT after playing a song then when kde starts up it says Xine was unable to initialize any audio drivers and it would play any music or anything i dont know if i screwed something up or what..And it just so happens im getting a new internet service tommorow and i wont be able to look up this problem for a mig chunk of the day tommorow so please help! =[

heres a screenshot of the error thingy

[http://img212.imageshack.us/img212/6366/snapshot6zm9.png](http://img212.imageshack.us/img212/6366/snapshot6zm9.png)

---

### Post by der_joachim on 2008-04-13
It seems that your audio drivers are not loaded. I got that issue after I had recompiled my kernel. I had just assumed that audio modules were to be compiled automatically, but they weren't. Temporarily reverting to the stock kernel fixed that issue for the time being.

To see which audio drivers are loaded, open up a terminal and give the following commands:
```

sudo -s
lsmod | grep snd
exit

```
The first command gives you temporary adminstrative privileges, the second command lists all loaded modules and filters all sound modules, and the third command exits admin mode.

---

### Post by N3um0rin on 2008-04-13
> **der_joachim said:**
> It seems that your audio drivers are not loaded. I got that issue after I had recompiled my kernel. I had just assumed that audio modules were to be compiled automatically, but they weren't. Temporarily reverting to the stock kernel fixed that issue for the time being.

To see which audio drivers are loaded, open up a terminal and give the following commands:
```

sudo -s
lsmod | grep snd
exit

```
The first command gives you temporary adminstrative privileges, the second command lists all loaded modules and filters all sound modules, and the third command exits admin mode.

I did it and put the password in for sudo but it didnt do anything...=[ Sorry im kinda a n00b at this

---

### Post by der_joachim on 2008-04-13
Hmmm... It sounds like no sound card was configured at all. What kind of sound card are you using?

---

### Post by medomedo on 2008-06-06
I have the same problem and its been for sometime. I run the command and here is the result:

snd_intel8x0           35356  3
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4868  0
snd_seq_oss            35584  0
snd_seq_midi            9376  0
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm

Any help is appreciated.

---

