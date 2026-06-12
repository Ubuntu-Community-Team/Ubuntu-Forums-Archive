---
title: "Hardy Scratchy Sound Problem"
date: 2008-04-24
forum: General Help
---

### Post by Vaelrith on 2008-04-24
I just upgraded to 8.04 from 7.10 using the Update Manager.  Now all sounds are scratchy and distorted.  Is it something to do with the new Pulse Audio?

---

### Post by DJI274 on 2008-04-24
I have the same problem, HP Pavilion dv6000, sound worked fine in Gutsy, very poor quality since upgrading to Hardy this morning, Any help much appreciated.
DJI

---

### Post by Vaelrith on 2008-04-24
I have the HP Pavilion dv9000 so probably same issue and same fix...

---

### Post by k-i-m on 2008-04-25
Me to.. Dv6000

---

### Post by ohhhchiahao on 2008-04-25
yup, dv2000 model here and im having the same issue. hopefully someone can figure this out soon.

---

### Post by Vaelrith on 2008-04-25
I've tried setting all the sound settings to use ALSA instead of auto detect and tried turning off software sound mixing but all have the same result of lots of static/distortion.  You may have better luck with that than I did, but this lack of sound is really annoying.

Alright I found out how to fix it from [COLOR="DarkOrange"][here](http://ubuntuforums.org/showpost.php?p=4274857&postcount=19)[/COLOR].  Basically, just right click on the volume control > click "Open Volume Control" then turn the PCM down a bit.  I turned it down to about 50% and the static went away then I turned it back up almost all the way and it works fine now.

---

### Post by PsychoMan on 2008-04-26
I have the scratchy sound problem, too. but I'm using a standard PC.
This "lowing PCM" solution doesn't work for me :/

---

### Post by k-i-m on 2008-04-26
Weee.. it solved my problem..

---

### Post by ohhhchiahao on 2008-04-27
wow, thanks a lot Vaelrith. i have been trying to find a fix for this annoyance ever since i upgraded to hardy and you've found a very simple solution to my complex problem. props to you

---

### Post by Vaelrith on 2008-04-27
> **ohhhchiahao said:**
> wow, thanks a lot Vaelrith. i have been trying to find a fix for this annoyance ever since i upgraded to hardy and you've found a very simple solution to my complex problem. props to you

Well I can't actually take full credit, I put a link to the thread I found it in.  I think it was in the hardy development testing thread.  Glad it's fixed for you though :)

---

### Post by kenfeyl on 2008-04-29
I think that fixed it. dv6000 here.

---

