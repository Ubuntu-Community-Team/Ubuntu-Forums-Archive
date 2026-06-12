---
title: "No Mic or Changing audio inputs in Lubuntu 14.04x64 for Realtek ALC887-VD"
date: 2014-06-01
forum: General Help
---

### Post by deamon_knight on 2014-06-01
I'm running Lubuntu 14.04 (upgraded from 13.10) on a Gigabyte G41MT-S2PT board, with integrated audio. ALSA reports this as a Realtek ALC887-VD sound device. My problem is that while the rear audio output works normally (I can play music, etc.). However, none of the other audio ports seem to work. The front panel audio out and mic do not work (no audio or mic capture) and the rear Mic also does not work, either in Skype or SoundRecorder. I've tried changing the settings in alsa mixer but haven't found a fix. Does anyone know how to fix this? Also if there is a good GUI utility for managing audio in and out from different front and rear audio ports?

Thanks

---

### Post by ajgreeny on 2014-06-01
In previous versions of Lubuntu I had to install pulseaudio and pavucontrol to get those things working properly.  I can not remember if Lubuntu 14.04 had PA by default, but if not try installing it and see if it helps you get things working.

---

### Post by deamon_knight on 2014-06-02
Hey, that worked! Thanks ajgreeny!

---

