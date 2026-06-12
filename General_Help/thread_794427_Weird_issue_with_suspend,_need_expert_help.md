---
title: "Weird issue with suspend, need expert help"
date: 2008-05-14
forum: General Help
---

### Post by HitRefresh on 2008-05-14
I installed 32-bit Hardy on HP DV6704nr laptop. Suspend/Hibernate was working fine out of the box. I then followed this post: [http://ubuntuforums.org/showthread.php?t=766529](http://ubuntuforums.org/showthread.php?t=766529) (#7) to get my wireless card to work. But now suspend/hibernate does not work, instead it hangs for a bit on black screen and then shuts down.

What is weird, is that to get the wireless to work, I had to **enable **"Support for Atheros Wireless" in the restricted drivers (that is not the HAL driver which is disabled). When I disable that in the restricted drivers - suspend/hibernate works like it should, but then wireless does not work anymore. 

I'm missing something here. I'm new to Ubuntu, but not to Linux. If someone could look at those steps in the post and see whats missing or could suggest something to try to get BOTH to work together.

---

### Post by zjunkie on 2008-05-21
I too have run into this problem, I haven't had much time to work on it but from what I have gleaned from google, something is horked up in the power management between the madwifi module and the wireless card. So far i haven't found a solution either, except to disable suspend for the time being.

---

