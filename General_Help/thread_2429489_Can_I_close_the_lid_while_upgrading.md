---
title: "Can I close the lid while upgrading?"
date: 2019-10-18
forum: General Help
---

### Post by bsykes3487 on 2019-10-18
So, I'm upgrading my laptop at school to 19.10, and I will need to close the lid soon (at 13:55 EST) to carry it between classes. Will closing the lid during an upgrade harm anything?

---

### Post by uRock on 2019-10-18
If it goes into suspend or hibernate, then it is likely to cause problems. Check your power settings.

---

### Post by bsykes3487 on 2019-10-18
How do you disable suspension upon lid close? I have checked power settings in the settings application and don't seem to see an option to change the action when the lid is closed. I have TLP installed, too, so maybe I can easily change suspend settings via that?

---

### Post by TheFu on 2019-10-18
Doing any patching while on battery is asking for problems.  Why tempt fate?  In no way would I attempt an OS migration on battery.

---

### Post by bsykes3487 on 2019-10-18
The battery is currently fully charged (in fact it's plugged in as I am writing this) and it will only be unplugged for around 5 minutes while I move classes, so I deducted I should be safe. This is a fairly new laptop (1-2 yrs old), so I have confidence it should survive long enough for me to move it. I have done similar upgrades on my old laptop, but had forgotten how I configured it to continue running while I moved it.

---

### Post by uRock on 2019-10-18
Here's the best thing I could find. I know there's a GUI way, but I don't use gnome on my laptop to find it and make screenshots. [http://tipsonubuntu.com/2018/04/28/change-lid-close-action-ubuntu-18-04-lts/](http://tipsonubuntu.com/2018/04/28/change-lid-close-action-ubuntu-18-04-lts/)

---

### Post by uRock on 2019-10-18
You may get an error with the sudo gedit command listed there, so replace that with ;```
sudo nano /etc/systemd/logind.conf
```then find the line for **HandleLidSwitch** and change it to **HandleLidSwitch=ignore**.
Hit Ctrl+x to exit nano, then "y" to save, then run ```
systemctl restart systemd-logind.service
``` which may need sudo in front of it.

---

