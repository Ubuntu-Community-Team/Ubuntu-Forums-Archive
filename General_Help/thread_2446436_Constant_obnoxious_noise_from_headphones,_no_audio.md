---
title: "Constant obnoxious noise from headphones, no audio [20.04]"
date: 2020-06-30
forum: General Help
---

### Post by faiuwle on 2020-06-30
I can't find anyone else with this exact problem, hopefully someone here can help.  I just installed 20.04 and when I use headphones there is a constant, loud, noise that sounds kind of like there's a key or something being held down which is generating an error sound.  It alternates between making this noise constantly and making no sound at all, if I try to play audio while it is making the noise, the noise stops but the audio doesn't actually get played.  There is absolutely no problem with the sound from the speakers, those seem to be working fine.  My headphones are not the problem, they can play audio in Windows and on my phone.

I've tried installing and checking pavucontrol, messing with alsamixer in various ways, etc.  Everything seems to be set up correctly, but clearly I'm missing something.

Thanks in advance.

---

### Post by faiuwle on 2020-06-30
Apologies for posting here prematurely - with a little more searching I was able to fix this.  The constant noise was apparently caused by the headphone microphone input being on - turning this off stopped the noise.  As for the sound not working, I managed to fix this by renaming ~./config/pulse to something else, rebooting, and letting a new ~./config/pulse be created.

---

### Post by haytham-med on 2020-06-30
U had a loop pulseaudio module on?

---

