---
title: "Screen Resolution problems...."
date: 2007-04-21
forum: General Help
---

### Post by takethepain on 2007-04-21
I recently installed Ubuntu only to discover that it wasn't using my LCD's native resolution of 1280x1024 but 1024x768. So I looked around for advice on how to fix this problem, backed up my xconf file as recommend and tried adding 1280x1024 manually to the xconf file. After restarting I realised this had not worked so  I used sudo dpkg-reconfigure xserver-xorg (another suggestion i found on the web) to attempt to fix my problem. Well after I changed a few values I restarted and the login window came up in the right resolution but when I logged in there were massive graphical glitches and was unusable. I restarted in recovery mode and reverted to my backup xconf file. The weird thing is that when I rebooted into Ubuntu at the login screen my screen was black with a message saying "input not supported", which i guess meant that it was running in a resolution that the monitor could not display. I was able to blindly type in my username and password however and when I logged in it displayed fine and when I went to the Screen Resolution control panel I could not only change my screen resolution to 1280x1024 (yay) but every other resolution that Ubuntu seems to support.

So what in the heck is going on and how can i get a useable resolution on my login window?

Thanks, Phil

---

