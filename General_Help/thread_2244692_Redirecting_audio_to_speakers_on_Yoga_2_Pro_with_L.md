---
title: "Redirecting audio to speakers on Yoga 2 Pro with Lubuntu 14.04"
date: 2014-09-18
forum: General Help
---

### Post by faure212 on 2014-09-18
I have a Yoga 2 Pro running both Windows 8.1 and Lubuntu 14.04.01.  On Windows everything works just fine, including the audio.  On Lubuntu, there is audio only from the earphones, but when I unplug the earphones the audio is not redirected to the speakers. 
I tried pulseAudio volume control, which shows that the output IS directed to the speakers, but no sound is heard from them.
I disabled the automute feature, using alsamixer, but that made no difference.
BTW-- changing the volume using the F2-F3 function keys, or the hardware side control both fail.

UPDATE: I installed the latest version of the ALSA driver (using DKMS), and got sound from the speakers.  However, once I rebooted, it was gone.... ;-(

What do I do?

thanks--

---

### Post by faure212 on 2015-05-01
This has bugged Yoga 2 Pro users for a long time, but it seems that the culprit has finally been identified-- there seems to be a ball at the earphone socket which is used in detecting whether an earphone plug is inserted.  That ball gets stuck, and can be freed by tilting the laptop and tapping on the socket.  Some people recommend using a CAIG Deox fluid.  Try it!

---

