---
title: "weather channel causes lockup"
date: 2015-05-23
forum: General Help
---

### Post by yonnie on 2015-05-23
When is this going to get fixed?  In case of lockup, what is the best method to get the system to un-lock?  Holding the power switch till system shuts down gives me cold-sweats.
By lockup, I mean everything except the mouse appears to have stopped functioning, including the clock on the panel.  

I've noticed this on 14.04 ubuntu unity, kde and Zorin 8, 9, even my Android phone.  Installing the FF weather channel add-on will cause it.  Browsing to the weather channel will cause it too.  Trying to add it to the kicker panel will cause it.  

Not having trouble with the wetter.com one.

---

### Post by TheFu on 2015-05-23
It is probably just the GUI (i.e. X/Windows), not the entire OS.
ssh in and kill X. That will restart the GUI.

---

