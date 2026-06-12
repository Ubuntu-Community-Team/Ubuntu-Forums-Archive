---
title: "Help, Ubuntu crashed and won't boot!"
date: 2007-10-01
forum: General Help
---

### Post by Karahana on 2007-10-01
This morning I woke up to a "out of frequency" message on my left X screen while my right X screen was still working OK. I rebooted and now X won't start any more. When I do a startx from the console, the system locks up and all I get is a black screen on both monitors. 

I tried to do a xorg.conf reconfigure with drivers from nvidia to nv with no success. Now I'm stuck and have no idea what to do! The installation is a weak old and I just finished configuring Ubuntu to my liking... :( Also I'm kinda pissed  since there's nothing I can do and I know there is something, but i just don't know it yet! :) Back on windoze now, please help my eyes are burning... Tnx! :D

---

### Post by ramjet_1953 on 2007-10-01
Not real sure about this, but when you set-up your partitions, did you give Linux plenty of room?

Regards,
Roger :cool:

---

### Post by Karahana on 2007-10-01
> **ramjet_1953 said:**
> Not real sure about this, but when you set-up your partitions, did you give Linux plenty of room?

Regards,
Roger :cool:


Well I did leave some torrents active overnight but my home partition was at 75% capacity... Ill  install the windoze driver for ext3 and check... Tnx for the idea! :) However this looks more like a driver problem to me, beacause of the "out of frequency" message. Neway, WEIRD... This is a windows like error...

---

### Post by kellemes on 2007-10-01
Yes, it seems to be a message from the monitor.. protecting itself against burn.
You should try to revert xorg-settings back to the vesa-drivers to at least get back in the game..

Have you tried "sudo dpkg-reconfigure -phigh xserver-xorg"

Edit: Always have a backup of /etc/X11/xorg.conf so you can place it back when things go bad.

---

### Post by Karahana on 2007-10-01
Ok, problem solved. It was REALLY REALLY weird. I'm guessing that GPU is failing or something. What I did was:

Booted into windoze and got a lock up every time I tried to open any kind of video file. Sat there guessing what to do. Decided to take out GPU and clean it up (you never know.. :) ) Did that with no success. Decided to unplug both monitors out of the GPU and booted like that. Plugged in one monitor only - resolution was set to something screwed up. FIxed it in windoze, tried to open a video file. Worked. Booted into Ubuntu with one monitor succesfully, then plugged in the other one, loaded a backed up xorg.conf, restarted X and here we are!

I'm really confused and shocked and have no idea WTF happened here. Smells like hardware problems, damn old GPU! It works now, thats what's important I guess... Tnx again for all your suggestions!

---

