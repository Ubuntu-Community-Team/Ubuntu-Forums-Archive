---
title: "Kubuntu, pmount, and disk space on mp3 players."
date: 2007-05-04
forum: General Help
---

### Post by MST3Kakalina on 2007-05-04
I recently bought a pretty ghetto mp3 player.  ZAP, if anyone else happens to be as cheap as I am.  50 USD for 1 gig flash memory + FM radio.  I don't need anything fancy.

I had a few problems mounting it at first, but worked around that with **pmount /dev/sdb**.

I loaded some music on it and went off fine and dandy. 

I went to add some more and at ~500 MB (at the moment, 532 MB; sometimes as low as 488 ) it caps out.  It won't let me copy any more songs, mainly because it thinks the disk is full (clicking around in Konqueror I eventually found a window that told me it was something like 98% full or whatever, but I'm too far gone at the moment to replicate it).  

I tried booting Gnome, figuring it might (somehow) be a KDE problem.  No dice. Boyfriend has the same model and he doesn't have this problem on Mandriva; I also tried with mine specifically to make sure.  So I'm pretty sure it's an Ubuntu-specific issue.

Is this an "I'm still on Dapper" problem? Or something else?  Help would be much appreciated.

---

### Post by dcstar on 2007-05-04
> **MST3Kakalina said:**
> I recently bought a pretty ghetto mp3 player.  ZAP, if anyone else happens to be as cheap as I am.  50 USD for 1 gig flash memory + FM radio.  I don't need anything fancy.

I had a few problems mounting it at first, but worked around that with **pmount /dev/sdb**.

I loaded some music on it and went off fine and dandy. 

I went to add some more and at ~500 MB (at the moment, 532 MB; sometimes as low as 488 ) it caps out.  It won't let me copy any more songs, mainly because it thinks the disk is full (clicking around in Konqueror I eventually found a window that told me it was something like 98% full or whatever, but I'm too far gone at the moment to replicate it).  

I tried booting Gnome, figuring it might (somehow) be a KDE problem.  No dice. Boyfriend has the same model and he doesn't have this problem on Mandriva; I also tried with mine specifically to make sure.  So I'm pretty sure it's an Ubuntu-specific issue.

Is this an "I'm still on Dapper" problem? Or something else?  Help would be much appreciated.

Check for any "hidden" directories or files (like the Trash).

---

