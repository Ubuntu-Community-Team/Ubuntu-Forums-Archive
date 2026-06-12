---
title: "Audacious MP3 player sounds better with equalizer disabled?"
date: 2015-02-24
forum: General Help
---

### Post by KayeNg on 2015-02-24
Hi guys.  I'm on the latest stable version of Lubuntu.  I've copied the Winamp presets, saved it with Leafpad in /home/mine/.config/audacious , then changed the interface of Audacious player to Winamp interface so I could load the presets.  But why is it that every preset sounds awful?  My music actually sounds better with the equalizer turned off.

What am I missing?  By the way, does it have anything to do with the PulseAudio that I've recently installed?

Thank you!

---

### Post by speartip on 2015-02-24
I ignore the presets. In all fairness, you shouldn't need to use an equaliser on a decent sound system, & everyones idea of the perfect sound is different.
What I do is enable the equaliser, & adjust the slides manually. In my case I just increase the bass slightly on the 1st 3 slides, ignoring the preamp. (keep that at 0)
Then tweak the crystaliser & extra stereo to about 1.0.
Perfect sound acheived. (In my opinion).

---

### Post by tgalati4 on 2015-02-24
Presets and Equalization in general uses software to manipulate the sound spectrum.  If your system has a lot of load or something that upsets the real-time processing of EQ, then your sound will be affected because of the distortion added.  If you have good speakers or headphones, then you can sometimes detect the EQ as adding a "muddy layer" to the sound.  If you have cheap, plastic, PC speakers, then EQ may be an improvement.

To see the effect of EQ, you need an oscilloscope and test it with pure sine waves.  You can see the distortion before you can hear it.  Try using mild EQ adjustments, rather than presets from Winamp.  There is nothing magical about EQ.  If your speakers lack high frequency or low frequency, you can add some back in--to a point.  If you have a dominant bass resonance in a room at 65 Hz, you can turn down the 63 Hz slider to compensate.

If you are listening to a podcast and it has too much high-frequency hiss, you can lower the treble (high frequencies) to make it less annoying.  If you like hip hop music with heavy bass, you can turn up the bass.  But if your amplifier and speakers can't handle the extra power, you will get distortion instead of extra thump.  Use EQ with care.  Turn it off if it does not improve the sound.

---

### Post by KayeNg on 2015-02-25
Thanks guys! I'll try your suggestion, speartip. Thanks!

---

