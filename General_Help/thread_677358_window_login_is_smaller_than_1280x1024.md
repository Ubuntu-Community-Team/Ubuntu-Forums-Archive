---
title: "window login is smaller than 1280x1024"
date: 2008-01-24
forum: General Help
---

### Post by bmesta on 2008-01-24
I have  a VGA compatible controller: Intel Corporation 82946GZ/GL Integrated Graphics Controller (rev 02). It's one of those Intel onboard graphic controllers.  But for some odd reason my login window is smaller than 1280x1024. How can i change these settings????

---

### Post by confused57 on 2008-01-24
> **bmesta said:**
> I have  a VGA compatible controller: Intel Corporation 82946GZ/GL Integrated Graphics Controller (rev 02). It's one of those Intel onboard graphic controllers.  But for some odd reason my login window is smaller than 1280x1024. How can i change these settings????
You could try removing any resolutions in your xorg.conf  that are higher than you're using on your Desktop...open a terminal(Applications---Accessories---Terminal), backup your xorg.conf:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

then edit the file:
```
gksudo gedit /etc/X11/xorg.conf
```
near the bottom of the file are your available resolutions, remove any resolutions higher than your Desktop resolution...quit & save.  Press Ctrl+Alt+Backspace.

If this doesn't work for some reason, you can restore your xorg.conf:
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

Note:  X is uppercase, then (one)(one)

Report back if this doesn't work, I think there is another method to change the dpi in your gdm configuration file.

---

