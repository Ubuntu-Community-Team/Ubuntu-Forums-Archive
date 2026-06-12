---
title: "Monitors won't go to sleep; only black screen and cursor"
date: 2016-09-26
forum: General Help
---

### Post by littlepinkus2 on 2016-09-26
Hello,

I'm running Ubuntu 16.04. My graphics card is a GTX 960 and I'm using the proprietary Nvidia driver version 367.44. Suspending the entire computer works just fine, as well does wake up afterwards. 

My problem is to put just my monitors to sleep. They are put to sleep after 5 minutes as specified in system settings, but after only a second or two they wake up again - but showing only a black screen with the cursor. If I wiggle the mouse or press a key, the login screen is presented. 

For information, I have tried ```
sleep 1; xset dpms force off
``` in an attempt to force the screen off, but same result.

---

