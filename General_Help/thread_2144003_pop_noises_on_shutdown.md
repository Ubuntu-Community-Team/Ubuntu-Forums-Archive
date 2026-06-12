---
title: "pop noises on shutdown"
date: 2013-05-10
forum: General Help
---

### Post by cir2633 on 2013-05-10
sorry for my poor english :p
  I recently purchased a Thinkpad T430 series laptop and dual booting(Ubuntu 12.04 and Win7).
  whenever I shutdown Ubuntu, I get a "pop noise" for about a second right before the machine actually powers off .
  I've tried a lot of linux os , and the same problem, pop noise on  shutdown. (For example ubuntu 12.04/12.10/13.04, Fedora 17/18, centos 6,  opensuse...)
  I doubt it's caused by alsa-driver, the drivers did not poweroff sound card before system shutdown.
  My sound card is "Realtek alc269" (detected by Everest on Windows), but in ubuntu, "aplay -l", it tell sound card is "alc3202"
  I got some information from [http://www.alsa-project.org/main/index.php/Detailed_HDA_changes_v1.0.24_v1.0.25#HDA_Intel_driver](http://www.alsa-project.org/main/index.php/Detailed_HDA_changes_v1.0.24_v1.0.25#HDA_Intel_driver) It looks like driver should turn "EAPD" off before shutdown.
  Any suggestions would be appreciated. Thank you.

---

