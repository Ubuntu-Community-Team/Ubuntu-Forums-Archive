---
title: "Lost login screen -Please help"
date: 2006-12-13
forum: General Help
---

### Post by lpeiris on 2006-12-13
I am running ubuntu 6.10. I had problems with sounds and I followed the thread [http://www.ubuntuforums.org/showthread.php?t=205449]("http://www.ubuntuforums.org/showthread.php?t=205449") and did following steps to fix the problem.
[LIST=1]
[*]sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
[*]sudo apt-get install linux-sound-base alsa-base alsa-utils
[*]sudo apt-get install gdm ubuntu-desktop
[/LIST]

Now when I start, I do not see the login screen, instead I get the tty screen. I have to type startx to open the GUI. startx do not send me to kde, it opens gnome. How do I get back the GUI login screen?
Thank you.

---

### Post by xopher on 2006-12-13
If you use KDE you might want to look into KDM instead of GDM, try installing it instead.

---

### Post by lpeiris on 2006-12-13
Once I login to gnome (through *startx*), I can go to kde using *startkde* command. But if I run *startkde* in tty, I am unable to open kde. I need to get the login GUI screen instead of tty screen.

---

### Post by taurus on 2006-12-13
```
sudo /etc/init.d/gdm start
```

---

### Post by lpeiris on 2006-12-13
I've tried the above command too. Still no luck. Please someone help...

---

