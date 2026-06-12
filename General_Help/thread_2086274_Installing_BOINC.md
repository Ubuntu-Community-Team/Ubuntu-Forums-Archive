---
title: "Installing BOINC"
date: 2012-11-20
forum: General Help
---

### Post by longbeard on 2012-11-20
Ubuntu 12.04 Pae, Some certainly stupid questions:

- I have downloaded BOINC software for SETI project but didn't get and surface for it nor was it listed in the program table. Uninstalled it again ..

- How can I modify settings for i) screen saver, ii) hibernation and other energy/switch-off settings? Don't appear in the "System Settings" panel!

---

### Post by zombifier25 on 2012-11-20
What is your question concerning BOINC?

As for power settings, try Power in System Settings. In order to enable hibernation, [see here](http://askubuntu.com/questions/94754/how-to-enable-hibernation). 

For screensavers, look in Brightness and Locks. If you want fancy screensavers, then install xscreensaver and the screensaver packs:
```
sudo apt-get install xscreensaver xscreensaver-data xscreensaver-gl xscreensaver-data-extra xscreensaver-gl-extra xscreensaver-screensaver-bsod xscreensaver-screensaver-dizzy xscreensaver-screensaver-webcollage
```
Remove packages that you deem unnecessary from the list. Then remove gnome-screensaver completely and add 'xscreensaver -no-splash' (no quotes) to Startup Application.

---

### Post by longbeard on 2012-11-20
My question about BOINC is: How can I use it? - I don't see it listed anywhere to start it, nor do I get hints about it.

---

### Post by QIII on 2012-11-20
Open the Dash and type "boinc" or use the terminal and do
```
boinc
```

What happens?

---

