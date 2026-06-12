---
title: "Problems after attempting to suspend."
date: 2007-12-29
forum: General Help
---

### Post by kneedeepinlife on 2007-12-29
I am running Gutsy with the ATI x1400 proprietary driver and XGL. I attempted to suspend my system, forgetting that it causes the system to hang.  Upon reboot, everything is running really slow. I am unable to start desktop effects and certain icons and text appears "scrabbled". Could it be a problem with the driver?

---

### Post by mandrill on 2007-12-29
you could try ctrl>alt>backspace, which will reset x.....it might not work, but it won't hurt anything....you may have to fiddle with the restricted drivers again, but it *should* work out.....

---

### Post by kneedeepinlife on 2007-12-29
I already tried restarting X. It didn't work.

---

### Post by kneedeepinlife on 2007-12-29
Ok, I ran through the steps to install the driver again and everything is running smoothly and I am able to run the desktop effects. However, the resolution is now lower than I usually run it. It's currently at 1280x1024. Anyone know how to fix this?

---

### Post by nick_h on 2007-12-30
You could try:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Make a backup of your /etc/X11/xorg.conf first!

---

