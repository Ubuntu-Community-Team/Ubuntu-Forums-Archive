---
title: "Freedb doesn't work with EAC"
date: 2007-04-06
forum: General Help
---

### Post by Rocklam on 2007-04-06
Hi,

I've just installed EAC and now that it finally works nicely, I can't get the CD information from Freedb. It worked for a while but then stopped working. I tried uninsalling EAC and configuring again but this didn't help. Depending on what freedb server I use from the list I get different error. Usually EAC gets really stuck and it might take for a very long time that it gives any error message. 

Do you have any ideas how I could get the track names to my files? 

I'd love to start ripping my cd collection but this is holding me back now. I'm also new to Ubuntu, so I've run out of ideas.

---

### Post by imasickboy on 2007-04-17
I had the same problem, and I suspect that it began with an update of WINE that I took. I think it may have been the 0.9.34 that was released March 30th. I have yet to test it by rolling back to 0.9.33, because I haven't had the time, but if you wish, try it yourself and let me know whether that is the issue. I strongly suspect that is the problem, though.

---

### Post by Rocklam on 2007-04-19
Thank you! I just went back to Wine 0.9.33 and freedb works again.

I already gave up all my hope couple of days ago. I had no clue it was a Wine problem, because I started using Wine and EAC when the new WINE update had just come but it must have been some update manager update that made it quit working in one point. I wasn't sure anymore if I had seen freedb work once or not (maybe I dreamed), but now I'm sure it really worked once before I lost it! 

Phew, now I go back to EAC.

---

### Post by imasickboy on 2007-04-19
Outstanding! I'm glad my hunch was correct, and you are up and running. I suppose a bug report needs filed with WINE, now. *sigh*

---

