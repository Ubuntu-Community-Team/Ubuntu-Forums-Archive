---
title: "Gaim no longer plays sounds"
date: 2007-01-28
forum: General Help
---

### Post by digby on 2007-01-28
As of a couple of days ago, gaim (2.0.0beta3.1) had stopped making any sounds.  Every other program (e.g. banshee, firefox, cedega, system sounds, vlc, etc) has properly functioning audio.

I checked the sound settings in gaim, and the source is set to automatic (as opposed to arts, esd, etc).  I tried each setting, but automatic is where it has always been set.  The .wav files that gaim uses are in /usr/share/sounds/gaim where they should be and all play fine in my media players.  I even tried pointing the program to them manually, but still no audio.

Running gaim from the terminal produces no errors when sounds should be played.

Any ideas?

---

### Post by djrenown on 2007-02-04
I have the same problem... ne one with suggestions?

---

### Post by CocoAUS on 2007-02-04
Have you checked to make sure that no other programs are open that might use sound?  Some people have had problems with Gaim's sounds when, for instance, Amarok is sitting in the system tray.

---

### Post by humansuit on 2007-02-05
I'm using beta 5 and the sounds just stopped working after upgrade, all I have in the options are console beep, command and no sounds. Selecting Command and using aplay %s works fine though.

Hope this helps

---

### Post by djrenown on 2007-02-06
thank you... works like a charm.

---

### Post by kolslorr on 2007-03-18
It doesnt work for me, doing aplay %s still produces no sound... :(

---

