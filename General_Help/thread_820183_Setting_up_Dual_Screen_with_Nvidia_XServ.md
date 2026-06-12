---
title: "Setting up Dual Screen with Nvidia XServ"
date: 2008-06-06
forum: General Help
---

### Post by Vigh on 2008-06-06
Hi, i've installed envy and graphics card drivers seem to be working A-Okay, now trying to set up a duel screen config, I can get twin-view to work, but in order to get the screen config I want, which is the seperate X-screen mode I have to restart and save the config file, when i go to save the save X configuration file, I get the following error, Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

---

### Post by chewearn on 2008-06-06
Run nvidia-settings with root permission:
```
gksudo nvidia-settings
```

Alternatively, save the xorg.conf file to your home directory, then manually copy it over using "sudo cp" command in terminal.

---

