---
title: "[SOLVED] Only have sound in one program"
date: 2008-05-29
forum: General Help
---

### Post by azizzle on 2008-05-29
For some reason, I now only have sound in Mplayer movie player, when it worked in all of my programs before. It also works on the internet, in youtube and break. How do I solve this problem??

---

### Post by unutbu on 2008-05-29
I'm guessing (mind you, this is only a guess) that there is an mplayer process that has failed to terminate and it is hiding in the background, unwilling to relinquish control of your sound card. 
To fix the problem, try terminating all mplayer processes by typing:

```
killall -s TERM mplayer
```

Edit: Does the problem go away if you reboot? If not, then ignore what I said above...

---

### Post by azizzle on 2008-05-29
Darn, no luck. Thanks though

---

### Post by unutbu on 2008-05-29
Does the problem persist after a reboot?

---

### Post by azizzle on 2008-05-29
yes

---

### Post by unutbu on 2008-05-29
So sound works with mplayer, youtube and break (is break a program?). What programs does it not work with?

---

### Post by azizzle on 2008-05-30
actually, I downloaded a vlc-alsa-plugin, and now everything works, vlc,mplayer,totem, EXCEPT rhythmbox.

---

### Post by azizzle on 2008-05-30
I solved this by opening up gstreamer-properties in the terminal and messing around with the settings. I don't know if the settings were changed or if i did something that no longer allowed the settings to work. I'm not sure. But it worked!

---

