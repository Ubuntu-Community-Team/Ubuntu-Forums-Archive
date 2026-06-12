---
title: "Load Ubuntu and just get background picture"
date: 2012-12-22
forum: General Help
---

### Post by Ericpode on 2012-12-22
Morning
Just Booted up Ubuntu, logged in and just see my rather nice scenic background picture and nothing else. Right clicking on screen gets a limited menu and I cancreate a new document or folder get into general settings and the file system. How do I get back the toolbars and buttons that I am used to.
I run a dual boot system with Windows XP. Last time I logged into Ubuntu I ran the update manager but did not update to the latest issue.
Eric

---

### Post by oldfred on 2012-12-23
Is this Unity without the bar on the left?

Does right click open anything?
Does alt-f2  or alt-f1 give a command line?
Can you boot from grub menu, recovery mode?

I had same issue with 12.10 and nVidia until I installed kernel headers and the nVidia driver.

---

### Post by Ericpode on 2013-01-20
Recovery mode gives same problem. 
Looks as if I have to install updated nVidia driver.
Eric

---

### Post by marin123 on 2013-01-20
You can try pressing Ctrl+Alt+F1 to get to console. From there you can log in with your credentials and run command
```
unity --replace
```

After that, press Ctrl+Alt+F7 to get back to your session. Unity should restart and you should be able to see the panel and the launcher.

---

### Post by Joao Lacerda on 2013-01-20
Hello friend,

The same happened here:
No sidebar, no menu on the top, the only way I have found to fix it, was right clinking 
on the desktop, choose "Change background", that will take you, to the "All Settings" too,then go the 
"Software Sources", "Additional Drivers" and check if you are using proprietary drivers. for me none of 
Nvidia drivers works, the only one that works beautifully is "Nouveau display driver 
from xserver-xorg-video-nouveau (open source)"
if you are going to Apply Changes made, you will need to reboot the system, 
Ctrl+Alt+T bring you the terminal. type sudo reboot.
I hope that it will works for you too.

Kind regards.

---

### Post by Ericpode on 2013-01-20
Thank you for the suggestions.
Problem sorted or more accurately changed.
Eric

---

