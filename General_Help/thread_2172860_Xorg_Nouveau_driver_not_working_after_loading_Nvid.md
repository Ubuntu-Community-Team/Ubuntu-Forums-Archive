---
title: "Xorg Nouveau driver not working after loading Nvidia 310"
date: 2013-09-06
forum: General Help
---

### Post by dani-valverde on 2013-09-06
Hello,
I've just recieved my new PC today and started tweaking it. I also have two monitors, one with VGA and the other with HDMI. By default my ubuntu distro (13.04) came with the Nouveau driver by default. I wanted to have the two monitors with independent desktops, so I switched to the Nvidia 310 driver (Software center > Edit > Software resources > Additional drivers). It loaded the driver and then everything went messy. First of all, my HDMI monitor is not getting any signal. Then, on the VGA monitor, I just see a plain desktop, no trays, no panels, just a plain Home icon. If I want to launch some program I have to do it from the terminal. I tried to switch back to the nouveau driver but the problem remained. Then I uninstalled all the Nvidia drivers (```
sudo apt-get remove --purge nvidia*
```) and double checked that I was using the Nouveau driver but nothing. Then, I checked the display section on gnome-control-center and I realized that it was being detected as a laptop. I've been struggling and searching for a solution for quite a few hours, but no luck. I'd like to say the before switching to the Nvidia-310 driver everything worked like a charm: 2 monitors, full resolution, compiz, ...
Can anyone help? I'm pretty hysterical right now.
Cheers,

Dani

---

