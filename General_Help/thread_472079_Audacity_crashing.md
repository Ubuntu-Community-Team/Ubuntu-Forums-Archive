---
title: "Audacity crashing"
date: 2007-06-12
forum: General Help
---

### Post by tubunu on 2007-06-12
I'm trying to record voice from a microphone while a background track is playing (ogg or mp3). Each time Audacity crashes at about the same point into the recording, usually around 30 seconds or so. Is there any bug fix for the crashing? Thank you.

---

### Post by tubunu on 2007-06-13
Has anyone else experienced frequent crashing of Audacity? Is there a way to improve its performance?

---

### Post by dabl on 2007-06-13
I've been using Audacity to record analog records (78 rpm and 33.33 rpm).  It doesn't crash for me, at least not much, although it has some other annoying "features".  But once I got the hang of it, it seems like a reasonably good tool for the purpose.  :)

---

### Post by atfrase on 2007-06-24
I have this problem too, except it's not just Audacuty (GNUsound, Sound Recorder, Ventrilo(wine) all do it, too -- anything that tries to open an audio capture channel it seems), and it seems to happen sooner (~5s after hitting 'record', even if I hit 'stop' before that point).  Hard system freeze -- alt-ctrl-f# doesn't work, have to totally power-off.

At first it happened with my onboard (via82xx) sound chip, which I have now disabled and installed a PCI SoundBlaster Live! Value (emu10k1) with exactly the same results: trying to record is a 5 second timebomb.

Feisty 7.04 clean download and install last week.  I've tried everything in the 'Comprehensive Sound Problem' guide such as --purge and reinstall, even tried recompiling the drivers (both standard Ubuntu package and bleeding-edge source from alsa-project), but both failed to compile (include/linux/pci.h errors).

---

