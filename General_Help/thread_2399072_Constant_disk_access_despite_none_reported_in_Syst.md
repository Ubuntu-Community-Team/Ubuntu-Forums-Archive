---
title: "Constant disk access despite none reported in System Monitor/Htop"
date: 2018-08-21
forum: General Help
---

### Post by solarliner on 2018-08-21
Hi,
This had been bugging me down for the latest weeks, my disk access LED sometimes stays constantly on and I can hear the disk spin on my laptop, however HTOP shows no disk activity, even with kernel threads enabled. The lapotop isn't swapping as I don't see the used swap metric change. This in turn results in degraded performance where trying to record a set in Mixxx lags both the UI and the sound output - where before with the same setup, I could go on hours non-stop without problems.

As a result of some Internet searches I decided to try changing the ext4 commit time from 5 seconds to 600, and while it helps most of the time and allows me some marginal battery life gains, it just doesn't help when Ubuntu starts to act up and constantly reads or writes to disk for no reason. Enabling disk cache changes nothing either.

My laptop is an ASUS R457UV.

What can I do to try and troubleshoot what is causing all that disk R/W besides the system monitor or htop which show nothing? Is this a known bug?

Thanks in advance.

---

### Post by oldos2er on 2018-08-21
I would try iotop.

---

