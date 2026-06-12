---
title: "Raspberry Pi 5 Sleep and HDMI blanking"
date: 2024-05-06
forum: General Help
---

### Post by silvergreen93 on 2024-05-06
Hi,

I have official Ubuntu 24.04 LTS installed on my Raspberry Pi 5.

Currently, the behaviour is that after 10 minutes of inactivity, the screen goes black, but the monitor is still on and draws full power as it does not enter sleep. I don't want this.



I want to know if it is possible to
1) Make the Raspberry pi sleep after 10 minutes of inactivity and then wake it by mouse, keyboard or power button
2) Make the HDMI monitor enter sleep mode after 10 minutes of inactivity.


Thanks!

---

### Post by MAFoElffen on 2024-05-07
It "should be'... But... Usually the display goes to sleep first, then after a time 'after' that... Other things goes to sleep. You need that time between. Not usually at the same time.

If this is not working with the settings menu, then trying by the setting in dconf, then you need to file a Bug Report on it, so that it get fixed for you and others.

I can't recreate this on the same Hardware right now. Mine is RaspPi4, not RaspPi5. At the moment, I can't afford to upgrade the hardware I have for RaspBerry. Sorry.

---

