---
title: "Login issue"
date: 2007-03-22
forum: General Help
---

### Post by nick_karstedt on 2007-03-22
Ok, had a slight problem with the latest nvidia drivers (x.org failed to start properly) but I got that fixed, but at the login screen, after I log in, it flickers (like it's changing resolutions) and then goes right back to the login screen.

---

### Post by taurus on 2007-03-22
Check the horizontal and vertical refreshing rates in /etc/X11/xorg.conf to make sure those values are right for your monitor.  You can get into a console with <Ctrl><Alt>F2.

```
sudo nano -Bw /etc/X11/xorg.conf
```
<Ctrl>o and <Ctrl>x to save and exit with nano.

---

### Post by nick_karstedt on 2007-03-22
hmm well I did a dpkg-reconfigure xserver-xorg earlier and everything checked out...

---

