---
title: "nvidia in 6.06"
date: 2007-07-15
forum: General Help
---

### Post by anv on 2007-07-15
I installed 6.06 (Dapper) yesterday. I tried to figure out how to get little bigger picture than 640x480 to my new 22" monitor, I wen't already through fact that nvidia-settings wont work with nvidia-glx and nvidia-glx-new is not found for dapper. så i even tried to fix my xorg.conf which I copied partly from my opensuse installation, but when restarting x, it had somehow changed values back to earlier and forget all my changes?!? any ideas how should I proceed I have also another monitor beside which I occasionally would like to use how this would be best to achieve? I considered to make couple of different xorg.conf files for different layouts and change them but as I mentioned ubuntu changed values without asking me first when I tried to do so so you who are wiser I need assistance here

---

### Post by Happy_Man on 2007-07-15
Perhaps you could use envy..... [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by anv on 2007-07-15
1. thank you. it solved installation of latest drivers

2. during installation I propably founded the original problem, I had saved one xorg.conf in my root folder, and copied it from there to /etc/X11 , it somehow lead in situation where my xorg changes were done to the original xorg.conf file in /root folder instead of /etc/X11/xorg.conf

---

