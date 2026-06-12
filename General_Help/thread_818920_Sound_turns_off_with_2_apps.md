---
title: "Sound turns off with 2 apps?"
date: 2008-06-04
forum: General Help
---

### Post by brycegg on 2008-06-04
Alright so I fixed a recent sound problem, but another arose.

If i play a game (Frozen-Bubble) and load Ardour (DAW) it says sound is being used. At the same time, if i watch YouTube, my aMSN turns off output for sounds.

If i run Frozen-Bubble with Ardour running, i hear no sound in the game..

Is this supposed to be normal?.. I've heard it is :(

---

### Post by tomcheng76 on 2008-06-04
it is supposed to be normal.
I guess some of the application are using OSS instead of ALSA sound driver.
if one of the application is using OSS to output sound, the sound device will be locked.

---

