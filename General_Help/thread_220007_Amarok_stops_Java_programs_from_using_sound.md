---
title: "Amarok stops Java programs from using sound?"
date: 2006-07-20
forum: General Help
---

### Post by Pichu0102 on 2006-07-20
I recently was playing music with Amarok, and all of a sudden, as soon as I hit play in Amarok, the game Puzzle Pirates could no longer make any sound, but Gaim still could.

How can I fix this?

---

### Post by Pichu0102 on 2006-07-27
Okay, I found it may be due to not having a soundcard that supports mixing.

Vendor: Intel Corporation
Device: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller

A logfile entry from the game reveals the device is in use, and can't work.

2006/07/24 13:40:27:069 ! media: Line not available to play sound [key=button_feedback, e=javax.sound.sampled.LineUnavailableException: Audio Device Unavailable].

How would I enable mixing?

---

### Post by Hikaru79 on 2006-11-09
Even with audio mixing, Java is notorious for not playing nice with the sound system; in Linux, I have never been able to get Java and anything else non-Java to use the soundcard together at the same time.

I'm not even sure if this is Sun's fault or ALSA's. *shrug*

---

