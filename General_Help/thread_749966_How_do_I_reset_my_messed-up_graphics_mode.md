---
title: "How do I reset my messed-up graphics mode?"
date: 2008-04-09
forum: General Help
---

### Post by rsilvers on 2008-04-09
I was trying to get 1680x1050 working on my Dell E1505. I was able to select that at 60 Hz by setting it to generic monitor/widescreen and then gemeric 1680x1050 LCD.

But the screen was scrambled. I can boot it in text mode. What file can I edit to reset the graphics back to 1280x1024?

---

### Post by sekinto on 2008-04-09
/etc/X11/xorg.conf

You can edit it with nano using the command:
sudo nano /etc/X11/xorg.conf

Or you can edit it with gedit if you boot from a live CD:
gksudo gedit /etc/X11/xorg.conf

---

### Post by Flying caveman on 2008-04-09
```
sudo dpkg-reconfigure xserver-xorg
```

Probably the first Linux command I've memorized

---

### Post by rsilvers on 2008-04-09
Thanks. I seem to be back up. Wish I could get 1680x1050 though! The best I can get to work is 1400x1050 but this display can do 1680.

---

