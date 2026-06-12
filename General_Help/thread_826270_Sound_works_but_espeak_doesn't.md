---
title: "Sound works but espeak doesn't"
date: 2008-06-11
forum: General Help
---

### Post by macroshaft on 2008-06-11
I have an Nvidia CK804 AC'97 sound card, initially the sound didn't work at all but random playing with the volume control settings brought it to life.

Generally all is ok but I discovered espeak today and when typing the command an error message is displayed 4 times

PaHost_OpenStream: could not open /dev/dsp for O_WRONGLY
PaHost_OpenStream: ERROR - result = -10000

---

### Post by joshsmith on 2008-06-13
espeak is an oss application, so you need to run it as
padsp espeak
to make it go through pulseaudio

---

