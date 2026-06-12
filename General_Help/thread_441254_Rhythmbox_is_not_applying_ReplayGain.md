---
title: "Rhythmbox is not applying ReplayGain"
date: 2007-05-12
forum: General Help
---

### Post by Frostmourne on 2007-05-12
On my Edgy install Rhythmbox played all my albums properly according to the ReplayGain values in the tags. Now on Feisty everything is playing at vastly different volumes even though the rhythmdb.xml file it has the ReplayGain values saved. Why isn't the new version of Rhythmbox using ReplayGain anymore?

Thanks for any help.

---

### Post by PvSinNL on 2007-09-15
Just stumbled upon this question as I was having the same issue after upgrading to Feisty. (Actually it was a clean install after a harddisk crash, but that's not the point here...)

Anyway, using **gconf-editor** I found a preference (under *apps* > *rhythmbox*) called "use_replaygain" that was disabled on my system. Enabling it restored Replaygain functionality in Rhythmbox.

---

