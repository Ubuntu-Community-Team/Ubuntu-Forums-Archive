---
title: "Totally ruined everything...graphics card/driver help"
date: 2008-06-17
forum: General Help
---

### Post by Gant on 2008-06-17
I don't know what the hell I did, but I basically screwed everything up. I wanted to run dual monitors using my TV as a second screen like I used to do with windows. I editing the one xconfig file and thought everything would be okay. However, just about everything that could go wrong did, and I'm now stuck on 800x600 resolution (with a 1440x900 monitor) and all my graphics settings are messed up.

Is there some way to just totally reset all my graphics settings, delete the drivers and go back to having my nice 1440x900 resolution? D:

---

### Post by manimal347 on 2008-06-17
>>xconfig file

Do you mean to say you fiddled with your Xorg.conf with a text editor, the X configuration file found at /etc/X11/xorg.conf? If so, and you have a modern (current driver tree/5-series+) Nvidia card, just run nvidia-xconfig. It will regenerate your xorg.conf. Make sure to back up the original (CP works). If you don't have an Nvidia GPU, or don't want to do this method, dpkg-reconfigure xserver-xorg will guide you through an ncurses GUI that rebuilds one geared to your system. Both methods may need some tweaks to fix issues where the canned xorg.conf files don't meet your system or needs. 

All this assumes you've subsequently looked in your xorg.conf and decided that the right resolutions were listed under your video device.

---

