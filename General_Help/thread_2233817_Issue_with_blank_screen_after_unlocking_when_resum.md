---
title: "Issue with blank screen after unlocking when resuming from suspend"
date: 2014-07-10
forum: General Help
---

### Post by ryan92 on 2014-07-10
Hey, I'm running a new install of 12.04 on my laptop and I'm having a weird issue with resuming from suspend.  It gives me the screen to unlock, but as soon as I do the screen goes blank and nothing ever comes up.  If I head over to tty1 and and pkill X it restarts and gives me the login screen, but after logging in the only thing I see is the background image and none of the rest of the interface comes up.

Some info in case it helps: My laptop is a Toshiba Satellite A505-S6986. I've got partitions for both windows and ubuntu both of which are fully encrypted.  My video card is a nVidia GeForce 230 M.

---

### Post by ryan92 on 2014-07-11
Alright, I figured out that the problem was the probably the nouveau driver for my video card.  I installed the latest nvidia driver (340.24) and disabled the nouveau driver and now everything seems to work just fine.

---

