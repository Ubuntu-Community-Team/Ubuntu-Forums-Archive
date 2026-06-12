---
title: "Envy won't install Nvidia driver because of XGL"
date: 2007-03-04
forum: General Help
---

### Post by FuturePilot on 2007-03-04
I was trying to install the latest driver on Dapper with Envy but it said the installation failed because it didn't recognize the xserver I was using or it was a different type of xserver. XGL. How do you get it to install with XGL installed?

---

### Post by FuturePilot on 2007-03-04
How did everyone else get it to work then?

---

### Post by bobbob1016 on 2007-03-06
If you have XGL installed, I am pretty sure you have the correct driver installed, but you can still run envy if you want.  Press Ctrl+Alt+F1 (it might just be Alt+F1, but Ctrl+Alt+F1 works too), this will log you out and put you in a terminal.  Then login, and type:
sudo envy -t
This will run envy in text only mode.  Envy should run fine now.

---

