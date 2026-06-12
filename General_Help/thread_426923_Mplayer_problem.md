---
title: "Mplayer problem"
date: 2007-04-28
forum: General Help
---

### Post by Balazs_noob on 2007-04-28
hi all

i would have a problem with my Mplayer
( just installed it because it was the best in Windows :)  )

 it always writes : "Error opening/initializing the selected video (-vo) device"

i have amd64 CPU but running 32 bit Ubuntu 7.04 because of flash support and stuff
lik that ;) ...

---

### Post by taurus on 2007-04-28
Start mplayer and go into Preferences and change the video from whatever it is right now to **xv**.  Exit and start it again.  Now, see if you can play a video with it.

---

### Post by Balazs_noob on 2007-04-28
Yeah it solved my problem :D
thanks ;)

---

### Post by jaywee on 2007-05-03
open terminal and run this command: 
gmplayer -vo x11 -ao oss
&#65292;it works,too!!

---

