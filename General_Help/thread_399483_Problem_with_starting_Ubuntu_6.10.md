---
title: "Problem with starting Ubuntu 6.10"
date: 2007-04-02
forum: General Help
---

### Post by Fendulon on 2007-04-02
I have recently tried to use a Ubuntu CD I burned at 4x. Everything goes fine, and I don't want to install at the moment, I am just trying to check out the OS, but it looks really promising. I have the exact same problem as this person in this thread, [http://ubuntuforums.org/showthread.php?t=359034](http://ubuntuforums.org/showthread.php?t=359034). I follow the directions to reconfigure the x-server, and it works... except I don't have video. I have the audio and I hear Ubuntu start after I type startx. I have tried several of the video drivers, entered several monitor names for my Dell P991 monitor. I have a custom computer that I made, I use a EVGA 8800gts. I entered my graphics card as a NVIDIA GeForce 8800 when it asked.

---

### Post by zvacet on 2007-04-02
When you run command to reconfigure X-server instead of **nvidia** try with** nv**.That should help.In case that failed try with** vesa**.After you get video search for drivers.It is Envy script.

---

### Post by Fendulon on 2007-04-02
Well, I do remember trying Nv and Vesa, but I will go try them again, is it required to enter the monitor and graphics card as I did? I am pretty confident it is, but not sure.

---

### Post by Fendulon on 2007-04-02
I have tried with both nv and vesa, but neither worked. I still get the same problem, I have no idea what it could be at this point.

---

