---
title: "Problem with Alsa and games"
date: 2008-05-21
forum: General Help
---

### Post by JTLenzz on 2008-05-21
Recently I have been having a problem with sound in games (both native to linux and in wine).  However sound with other applications has been unaffected (such as Ekiga).  I tried running StepMania in the terminal and this was the output:

```
user@computer:~/.StepMania-3.9$ ./stepmania
StepMania 3.9
Log starting 2008-05-21 21:43:52
Loading window: gtk
OS: Linux ver 020624
Crash backtrace component: x86 custom backtrace
Crash lookup component: dladdr
Crash demangle component: cxa_demangle
Runtime library: glibc 2.7
Threads library: NPTL 2.7
TLS is available
ALSA: Advanced Linux Sound Architecture Driver Version 1.0.16.
ALSA Driver: 0: HDA Intel [Intel], device 0: AD198x Analog [AD198x Analog], 0/1 subdevices avail
ALSA Driver: 0: HDA Intel [Intel], device 1: AD198x Digital [AD198x Digital], 1/1 subdevices avail
Couldn't load driver ALSA: dsnd_pcm_open(hw:0): Device or resource busy
Mixing 0.000000 ahead in 0 Mix() calls
Couldn't load driver ALSA-sw: dsnd_pcm_open(hw:0): Device or resource busy
Mixing 0.000000 ahead in 0 Mix() calls
Couldn't load driver OSS: RageSound_OSS: Couldn't open /dev/dsp: Device or resource busy
Language: english
Theme: XIII+
Error: Couldn't find a sound driver that works

```

Does anyone know what the problem could be?

---

