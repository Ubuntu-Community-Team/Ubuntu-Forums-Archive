---
title: "xmms/beep crashing, or not playing songs"
date: 2005-04-21
forum: General Help
---

### Post by james_mad on 2005-04-21
Everytime I try to play my playlist in xmms or beep it crashes.  I launch xmms, or beep, clicked to add all my music files, double click on a track, and it crashes.  And if I try to press the play button it just sits there without any sound and without moving anything, and I know my sound works.  Is there something wrong with the programs?  Or am I doing something wrong?  Also, how do I force quit a program from the terminal?  Thanks.

---

### Post by NeoChaosX on 2005-04-21
Check the audio output plugin used by either program. In Beep, it's Preferences -> Plugins -> Output, in XMMS it's Preferences -> Audio I/O Plugins. Check whether it's using OSS, ESD or ALSA, and try changing it to one of the others to see if it fixes your problem.

---

### Post by james_mad on 2005-04-21
That sounded crazy enough to work... and it did, sweet!!!  Thanks  :grin:

---

