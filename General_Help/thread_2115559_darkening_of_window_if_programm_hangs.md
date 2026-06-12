---
title: "darkening of window if programm hangs"
date: 2013-02-13
forum: General Help
---

### Post by mks333 on 2013-02-13
Is there a way to turn off the "darkening of a window" when it hangs?
The thing is that I wrote a programm which just needs a lot of time to calculate stuff, and i don't want that it gets "darkened" during calculations.

Hope you know what I mean

thx in advance, mks

---

### Post by The Cog on 2013-02-13
I believe that the proper thing to do is to perform the long-running calculation in a separate thread, leaving the GUI code free to respond to the GUI events as normal.

---

### Post by ksprasad on 2013-02-13
Hi,
 
Sometimes back I had seen some settings in CompizConfig Settings Manager. Something like "Dim Unresponsive Windows" under "Fading Windows". Not sure if its still there.
 
Regards,
ksprasad

---

### Post by mks333 on 2013-02-13
yes seperating the calculation in an own thread would be the best thing, but at the moment i can't do that and i just wanted to have a quick workaround... ;)

i'll try this compiz setting manager.

thx meanwhile!

---

