---
title: "[B]nvidia-settings taskbar shortcut ICON NEEDED [/B]"
date: 2006-12-31
forum: General Help
---

### Post by fokuslee on 2006-12-31
i followed tseliots guide to add a menu bar shortcut for nvidia-settings

sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA X Server Settings
Exec=nvidia-settings
**[COLOR="Red"]Icon=[/COLOR]**
StartupNotify=true
Terminal=false
Type=Application
Categories=Application;System;

now i want a nice nvidia-logo to be displayed as the shortcuts icon
How should i do it? 
Thanks

---

### Post by ThrobbingBrain66 on 2006-12-31
[http://www.nvidia.com/content/areyouready/downloads.html](http://www.nvidia.com/content/areyouready/downloads.html)

download the icons to your home directory and unpack them.  then right-click the shortcut and choose properties.  then click th icon box and navigate to the icon you want and select ok.

---

### Post by fokuslee on 2006-12-31
hehe i mean the item under applications>system tools> nvidia-settings on the top menu bar
Here is whats really interesting 
i can create a desktop shortcut and change the desktop icon to any png img i like.  (i don't think ubuntu take ico files)
i even put a png icon i found in /usr/share/app-install/icons/ 
and put Icon= that file location
still no success.  
grrr soo frustrating lol 
any ideas

---

