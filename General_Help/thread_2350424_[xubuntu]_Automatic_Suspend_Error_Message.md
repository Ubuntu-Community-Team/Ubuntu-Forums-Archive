---
title: "[xubuntu] Automatic Suspend Error Message"
date: 2017-01-24
forum: General Help
---

### Post by blomstertj on 2017-01-24
I have Power Manager set to put my computer to sleep after an inactivity period.  However, when it does that it brings up an error and does continue to suspend.  I can suspend by closing the lid and by using the keyboard shortcut on my laptop.  

Here's the error: [ATTACH=CONFIG]273360[/ATTACH]

Specs:
Xubuntu 16.04
Model: HP EliteBook 840 G2

EDIT: I was able to fix it by running this command ```
xfconf-query -c xfce4-power-manager -p /xfce4-power-manager/inactivity-sleep-mode-on-battery -n -t int -s 1
```

That I found from this thread: [https://forum.xfce.org/viewtopic.php?id=9810](https://forum.xfce.org/viewtopic.php?id=9810)

---

