---
title: "Crackly sound recordings"
date: 2005-06-29
forum: General Help
---

### Post by petehall on 2005-06-29
Whenever I record sound in Ubuntu the results have a persistent crackle running through them. This happens whether I use Audacity or the standard Sound Recorder, and whether I'm recording from the line-in socket on the sound card or an MP3 playing on XMMS at the time.

The mixer offers me the choice of "Realtek ALC100/100P rev 30 (OSS Mixer)" or "SiS SI7018 (Alsa Mixer)" - both result in the crackle.

My motherboard is an SiS-730 with built-in sound and video, and I don't get the problem with Windows. I have no problems at all with playback. Does anyone know of any possible causes or solutions to the problem? If I can get this sorted out, it will pretty much remove my need to ever use Windows again.

I've put a sample at [http://www.pete.nu/downloads/cash.ogg](http://www.pete.nu/downloads/cash.ogg)

---

### Post by petehall on 2005-06-30
(bump)

---

### Post by petehall on 2005-07-09
Some progress on this - I've discovered the Multimedia Systems Selector in System > Preferences which allows you to change the input source from OSS to ALSA. The crackle is gone, and the sound quality is better by a great amount, but it still seems a little disappointing.

I also tried the ESD option but it caused the sound recorder to hang, so I let that one go.

---

### Post by petehall on 2005-10-20
Further update - I've got a new motherboard (MSI K8MM-V) and the quality of the sound recorded is exceptional. I blame the problems with the SiS motherboard on bad driver support.

---

