---
title: "How to disable login sound at startup (Ubuntu 13.10)"
date: 2013-12-04
forum: General Help
---

### Post by ijhm86 on 2013-12-04
So the volume is up to 100% everytime I turn the computer on.

I want to disable both the login screen sound and the system volume. I want it to be muted by default when I turn the system on.

I have seen ways to do it in previous Ubuntu releases, but I can't find the way to do it in the current release.

Thanks in advance.

---

### Post by philinux on 2013-12-04
Top left big icon Dash > type in startup

Open startup applications. Untick login sound.

Click on the volume indicator top right and choose your preferences.

---

### Post by ijhm86 on 2013-12-04
Hey philinux! Thanks for your reply.

But I had already tried that. There is no "Login Sound" there. I can only see "Diodon", "my-weather-indicator-autostart", "System Load Indicator" and "Variety".

---

### Post by sammiev on 2013-12-04
System settings --> Sounds --> Sound Effects.

---

### Post by deadflowr on 2013-12-04
In the file 
> /usr/share/gnome/autostart/libcanberra-login-sound.desktop
is the line 
> X-GNOME-Autostart-enabled=
marked as true or false?
If true, open the file as root and change it to false.
TO view the file easily, run
```
gedit /usr/share/gnome/autostart/libcanberra-login-sound.desktop
```
and with root, use gksu in front, like sudo commands would.

---

### Post by ijhm86 on 2013-12-05
Thanks for the replies!

I did as sammiev said. It was there, under Sound Effects. I just had to mute the alerts and also mute the system sound. I restarted the computer and no sound was played (obviously, it couldn't since I set the volume to 0%).

I also checked what you told me deadflowr. It is now "FALSE". I guess it was "TRUE" before I changed anything in the System Settings.

Thank you all for your help!

---

