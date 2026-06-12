---
title: "Well this is odd! - nVIDIA"
date: 2007-04-24
forum: General Help
---

### Post by BrokeBody on 2007-04-24
I didn't want to install the proprietary nVIDIA driver via Restricted Drivers Manager from the Administration menu. I wanted to install it and set it up manually:

sudo apt-get install nvidia-glx
sudo gedit /etc/X11/xorg.conf

After that, I switched "nv" to "nvidia" and restarted X.

After the restart the X was broken and I couldn't start X. With nano editor I changed "nvidia" back to "nv" and then I started X normally. I had to run Restricted Drivers Manager after that  and to check "Enable". I restarted the system and after that I checked my xorg.conf.

In xorg.conf everything was the same, just like when I was trying to set it up manually - instead of "nv" there was "nvidia", but now it works! Isn't all this the "same" thing?!?

Really odd! :confused: 

:-k

---

### Post by energiya on 2007-04-25
I think you should have also installed nvidia-restricted-modules. Try searching using Synaptic or aptitude for "nvidia".

---

### Post by BrokeBody on 2007-04-25
It was already installed.

---

### Post by spankymasterc on 2007-04-25
sudo dpkgs-reconfigure xserver-xorg   try that and redo your X

you can choose Nvidia there instead of NV or what ever ..... 

::cheers::

---

