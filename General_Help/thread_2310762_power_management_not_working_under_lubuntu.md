---
title: "power management not working under lubuntu"
date: 2016-01-21
forum: General Help
---

### Post by rebeltaz on 2016-01-21
I have lubuntu 14.04LTS installed on a system with xfce power manager set to start automatically. I have sleep disabled, lock screen disabled, screen saver disabled... yet the monitor keeps shutting off and the system keeps going to sleep. I use this with a KVM switch and it refuses to wake back up when I switch back. Can someone tell me what I am doing wrong? Thanks.

[ATTACH=CONFIG]266880[/ATTACH]  [ATTACH=CONFIG]266881[/ATTACH]  [ATTACH=CONFIG]266882[/ATTACH]  [ATTACH=CONFIG]266883[/ATTACH]

Still looking for this if anyone can help. Thanks.

Sure, Derek... what you need to do is go to "Preferences > Default Applications For LXSession". On the left hand side, click on "Core Applications". Delete anything in the text fields next to "Screensaver" and "Power Manager". Next, click on the "Autostart" tab on the left. Make sure that "Power Manager" and "Screen Locker" are unchecked. Close the "LXSession Configuration" window and then reboot the system.

Awesome! Thank you so much. Worked like a charm!

---

