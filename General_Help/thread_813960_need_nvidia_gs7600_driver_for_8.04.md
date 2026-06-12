---
title: "need nvidia gs7600 driver for 8.04"
date: 2008-05-31
forum: General Help
---

### Post by errolgreer on 2008-05-31
****I had 7.10 running with dual screens with my Nvidia gs7600 card. I now need the correct driver to download and install for 8.04. - Please help !

Errol**:(**

---

### Post by Nepherte on 2008-05-31
You can install the nvidia drivers in the restricted driver manager:
system > management > restricted drivers

---

### Post by quelx on 2008-05-31
> **Nepherte said:**
> You can install the nvidia drivers in the restricted driver manager:
system > management > restricted drivers

once you do this, run in a terminal:

```
sudo apt-get install nvidia-settings
``` 

and you'll get a control panel for your displays

---

### Post by errolgreer on 2008-05-31
****I ran the sudo apt-get install nvidia-seetings command, - it did a few things etc but no configuration menu or window came up. It is enabled, but how to I get a menu to allow me to set up the 2 screens ? Only the first screen is active. When I boot, both screens are active, so the hardware is working, but after booting only one is active. I had both screens running in 7.10, but the 8.04 install overwrote 7.10 completely.****

---

### Post by diablo75 on 2008-05-31
> **errolgreer said:**
> ****I ran the sudo apt-get install nvidia-seetings command, - it did a few things etc but no configuration menu or window came up. It is enabled, but how to I get a menu to allow me to set up the 2 screens ? Only the first screen is active. When I boot, both screens are active, so the hardware is working, but after booting only one is active. I had both screens running in 7.10, but the 8.04 install overwrote 7.10 completely.****

You'll want to run this control panel you just installed from terminal as sudo.  So:

```
sudo nvidia-settings
```

Then be sure to save the changes to the xorg.conf file with the Save button at the bottom when you're done.

---

