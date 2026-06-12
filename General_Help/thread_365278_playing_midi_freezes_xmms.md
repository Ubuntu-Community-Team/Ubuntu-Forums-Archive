---
title: "playing midi freezes xmms"
date: 2007-02-19
forum: General Help
---

### Post by AGSzabo on 2007-02-19
when i play a midi with xmms (plugin and timidity is installed) i can hear the correct sound output BUT xmms freezes immediately so that i can only switch its window from front to back or from back to front but no button works and cannot quit.

---

### Post by qpwoeiruty on 2007-03-19
Same here, have to forcefully quit xmms to do anything else on the system.

---

### Post by wpshooter on 2007-03-19
I have tried many times to get Midi files to play on my Ubuntu systems (with a program that has a GUI) and I have not had any luck yet in ever getting it to work.

---

### Post by gubbins on 2007-04-16
Try switching your output plugin from alsa to oss. It worked for me. Now it doesn't freeze, it just lags a  little. But I'm in Debian testing not Ubuntu.

---

### Post by giltwist on 2007-05-26
Confirming that switching to OSS fixes the problem.

---

### Post by raydar on 2007-10-23
I just ran into the same problem, hunting for a simple way to play midi.  I'm using UbuntuStudio, so you'd think that might come easier, but no.  I suppose I could try switching to oss, but geez; isn't that the tail wagging the dog?  

Not to knock XMMS out of hand, but I'm more into a spectrum analyzer or musical score look than a car stereo look, so I'm going to try Playmidi instead (dunno what it looks like).  Main reason I installed XMMS first was I found the "xmms-midi" plugin already installed for some reason.

EDIT:  Okay, no gui at all with playmidi, though I'm sure it probably works fine.  So I installed Kmid, and it's exactly what I was looking for . . . including not crashing , , . I did have to go to its Settings menu and choose a different MIDI device than was selected by default; it was a pretty long list, which could be daunting for a new user, but I just chose the first Timidity entry and that worked.  (Specifically, "TiMidity TiMidity port 0 - ALSA device" gave me sound, which the default "Midi Through Midi Through Port-0 - ALSA" [typed as it appears] did not.)

---

