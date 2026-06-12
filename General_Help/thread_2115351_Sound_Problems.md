---
title: "Sound Problems"
date: 2013-02-12
forum: General Help
---

### Post by disabled20191128 on 2013-02-12
Hi,
I am experiencing some sound problems, each two seconds approximately I hear weird noises coming from my speakers, crackling, popping etc... 
In  Sound Settings, under the output tab i can see a digital output, an analog output and each two seconds the headphones output that appears briefly then goes away (my headphones are disconected). It seems to be affecting the master volume, because it goes up and down.
It is starting to get on my nerves, so please help me.

PS It is not a hardware problem because everything works perfectly on windows

---

### Post by disabled20191128 on 2013-02-12
Anyone?

---

### Post by dabl on 2013-02-12
```
lspci -vvnn | grep audio
```

```
aplay -l
```

```
lsmod | grep snd
```

---

### Post by Yellow Pasque on 2013-02-12
@dabl: it's better to ask for full ALSA info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by disabled20191128 on 2013-02-12
Here it is!

[http://www.alsa-project.org/db/?f=9421279acc59f6000dc7bfc33918d50757c81d87](http://www.alsa-project.org/db/?f=9421279acc59f6000dc7bfc33918d50757c81d87)

---

### Post by Yellow Pasque on 2013-02-12
My recommendation would be to test latest ALSA drivers: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
If it's still a problem with the latest drivers, file a bug.

---

### Post by dabl on 2013-02-12
Nice one -- thanks Temüjin!

---

### Post by disabled20191128 on 2013-02-21
It is still not working as it should, even after the update, what now?

---

### Post by Yellow Pasque on 2013-02-21
File a bug:
```
ubuntu-bug alsa-base
```
After it gives you a link to your bug, attach the pulseaudio log: [https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)

---

