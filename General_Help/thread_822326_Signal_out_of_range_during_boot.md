---
title: "Signal out of range during boot"
date: 2008-06-08
forum: General Help
---

### Post by Pi72 on 2008-06-08
Hi people.

I used to have a GeForce MX200, until this week a friend gave me his old Asus A9200 (Ati based). I replaced the card, and after a few headaches I configured it properly. Both the monitor and the card are properly configured and working fine.

However I get a "signal out of range" in my monitor while booting. When the Ubuntu logo and the progress bar of the system loading should appear, I see nothing. When I get to the splash screen, I can see it well, then I can work in Ubuntu perfectly. Same happens when I power off the system, and after running the scripts, when the Ubuntu logo should appear again with the progress bar for shutting down, the "signal out of range" appears again.

I'm guessing this has nothing to do with xorg.conf, right? So, where should I look at for changing the resolution for the booting progress bar?

---

### Post by Pjotr123 on 2008-06-08
Try this:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 3 )

---

### Post by Pi72 on 2008-06-08
Thanks, that did it. I just had to change the resolution in the usplash file. Apparently the card doesn't support high resolutions before the xorg drivers are loaded.

---

