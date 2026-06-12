---
title: "Unable to move files on Android phone from Ubuntu"
date: 2015-11-01
forum: General Help
---

### Post by jsleotti on 2015-11-01
This is a little thing, but kind of annoying. I can read, copy to, and delete files from my phone when connected to the USB port -- but if I want to move from one folder to another -- I get "error - unsupported operation". It seems rather odd that I can do everything else, but not that. Since I can write to it I'm assuming it's not mounted as read-only. I dunno, it's odd. Any thoughts are appreciated. Again, not the biggest problem, but it would be a little faster to organize my music and photos via the computer.

---

### Post by TheFu on 2015-11-01
I've seen this too, but only with MTP connections.
Whenever I open a terminal on the android device, **mv** worked fine last time I did it. It has been over a year. Switched to a different way to get files onto my devices since then.

---

### Post by DK1993 on 2015-11-02
Have you tried enabling USB Debugging on your Android device? I've had a issue similar to this and that seemed to fix the issue for me in the past. To do this you need to go to Settings > About and tap Build Number about 7 times until it says Developer Options enabled or something along those lines. Then go into the newly created Developer Menu and enable USB Debugging. I think it changes permissions to allow movement of files directly to the phone. YMMV and this shouldn't compromise the security of the phone, but I do advise switching it off when done.

---

### Post by TheFu on 2015-11-02
Dev mode didn't matter on any of my android devices.

---

### Post by jsleotti on 2015-11-02
USB debugging did not change anything for me. I also tried gMTP, but all that happens is the screen goes grey when I hit 'Connect'.

---

