---
title: "only gdm3 appears to work on laptop upgraded to 17.10"
date: 2017-10-21
forum: General Help
---

### Post by jamesjones01 on 2017-10-21
I switched to gdm3 (help much appreciated), but gdm2 and GNOME shell share an issue I had on Cinnamon in 15.04 (haven't checked it on 17.10 yet), namely the screen rotates at some multiple of 90 degrees with no action on my part and no motion of the laptop. I thought I'd try sddm. I did so, and chose sddm when prompted to choose a desktop manager.

That done, I rebooted... and found that I didn't get the sddm login screen. The screen where it should have appeared showed the "kubuntu" splash screen, and then went blank. I tried a couple more times, and this is what /var/log/sddm.log looked like. [ATTACH]277186[/ATTACH]

I ended up reinstalling gdm3 (i'd removed it to see whether that helped--it didn't), and now I can log in graphically again. I will try GNOME shell to see whether it rotates as well (I read that gdm actually starts a GNOME shell, so I suspect a GNOME shell session will rotate as well) and live with the rotation for now. Of higher priority is figuring out why the laptop takes about 51 seconds from entering the password to the appearance of the session. (I created a new account to see whether it was some configuration file in my home directory that needed changing, but the new test account has a similar delay.)

---

### Post by wildmanne39 on 2017-10-21
Thread moved to general help because 17.10 has been released it is not in development anymore.

If you need help please be concise with your question it will be easier to know exactly what you need help with.

I thought gdm2 has been dead for a long time, it is a big step from gdm2 to gdm3 it is best to do a fresh install.

---

### Post by jbicha on 2017-10-22
To turn off screen auto-rotation, open the system status menu in the right of the top bar. Click the button at the bottom with a rotated rectangle icon to lock or unlock screen auto-rotation.

---

