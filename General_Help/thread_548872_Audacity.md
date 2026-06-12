---
title: "Audacity"
date: 2007-09-11
forum: General Help
---

### Post by Tyke91 on 2007-09-11
I don't seem to have any options to choose an playback device in audacity... my music and things work just fine in other programs, but i'd like to edit them... so far, all i've gotten is an error message saying that there was an error opening the soud device and that i should check my output device settings and sample rate.

what's going on?

---

### Post by por100pre1 on 2007-09-11
Read [this]("http://audacityteam.org/wiki/index.php?title=Linux_Issues#Error_Initializing_or_Opening_Sound_Device"). Hope it helps. :)

---

### Post by hilltop_yodeler on 2007-09-15
por100pre1, thanks for posting that link.  For some time now, I've been working on figuring out why my Playback Device would not work in Audacity, but works fine in everything else.  Disabling the eSound (ESD) server in the Sound Preference Panel did the trick.  Not only can I hear the audio playback now, but /dev/dsp now also shows up as a playback device in Audacity's preferences.  Anyway, thanks for pointing me to the solution, and thanks to the audacityteam wiki.
[http://audacityteam.org/wiki/index.php?title=Linux_Issues#Error_Initializing_or_Opening_Sound_Device](http://audacityteam.org/wiki/index.php?title=Linux_Issues#Error_Initializing_or_Opening_Sound_Device)

---

