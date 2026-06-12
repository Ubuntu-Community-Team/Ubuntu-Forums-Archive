---
title: "monitor resolution problem"
date: 2006-11-03
forum: General Help
---

### Post by Sterbik on 2006-11-03
My machine only works on 1280x1024 61Hz, and when I try to set it on 1024x768 it throws me bock into the Log In menu, and when I log in it is reset to 1280x1024 61Hz.
I need help!

---

### Post by taurus on 2006-11-03
You can delete that high resolution in /etc/X11/xorg.xorg or you can always reconfigure your X and pick the resolution that you want to use.

To edit it:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
gksudo gedit /etc/X11/xorg.conf

```

To reconfigure X again:
```
sudo dpkg-reconfigure xserver-xorg
```

---

