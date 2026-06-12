---
title: "[SOLVED] monitor shuts off, no power saving enabled"
date: 2013-05-17
forum: General Help
---

### Post by pickarooney on 2013-05-17
Since upgrading to 12.04 yesterday (Xubuntu) my  monitor keeps shutting off after 10 minutes. My power saving settings are all at 0 and DPMS is disabled. 

Where else might I look to disable this?

---

### Post by dentaku65 on 2013-05-17
Try to edit xorg.conf
```
sudo nano  /etc/X11/xorg.conf
```
And add this section
> Section "ServerFlags"
Option "BlankTime" "0"
Option "StandbyTime" "0"
Option "SuspendTime" "0"
Option "OffTime" "0"
Option "DontZap" "false"
EndSection 
Reboot

---

### Post by pickarooney on 2013-05-18
That seems to have sorted it. Thanks!

---

