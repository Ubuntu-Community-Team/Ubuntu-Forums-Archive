---
title: "Constant freezes"
date: 2008-04-09
forum: General Help
---

### Post by Lederallergie on 2008-04-09
I'm pretty much a noob with ubuntu, so don't get angry if I don't use the right terms :P

My laptop keeps freezing up every 10 minutes or so. It freezes for a minute or two, then starts working again. This happens regardless of which programs I have running. When I check the system monitor graphs, it looks like the CPU curve just goes down to zero when this happens, as if it just stopped working.

Hope someone can help me.

---

### Post by HermanAB on 2008-04-09
There is a known problem with HAL and some old CDROM drives, causing annoying periodic freeze-ups.  You can try killing the 'halld-addon-stor' process and see whether the issue goes away (it won't affect anything else if you kill this process):

This will show the HAL processes:
$ ps -e | grep hal

This will kill the problem child (check my spelling from the above list!):
$ sudo killall halld-addon-stor

Check again to see if it stopped:
$ ps -e | grep hal

Cheers,

Herman

---

### Post by Lederallergie on 2008-04-09
Thanks a bunch, I'll try that :D

---

