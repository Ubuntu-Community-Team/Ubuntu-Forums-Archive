---
title: "Alsa a no go with esound..."
date: 2005-03-29
forum: General Help
---

### Post by Polymira on 2005-03-29
Ok, so it looks like the Enlightenment Sound Daemon is running when i boot up, so i think to myself "cool, that means i can play more then one sound at once when running, neato" ... but then when starting certain apps that require alsa, they can't use it and error out, so if i kill esd, it all works well, but only one sound at a time (one app using sound shall i say)... and work arounds?

---

### Post by sinbad782 on 2005-04-11
I had a similar experience with XMMS - I had to set it to use the esound plugin and not ALSA. Also, there doesn't seem to be a midi device displayed in KDE control panel even though sound otherwise works. 

I am using the built-in nforce2 sound card on my motherboard and I believe the ALSA driver is the intel8*0 or so. 

I am not very well versed in linux sound architectures, but this is very strange...

---

