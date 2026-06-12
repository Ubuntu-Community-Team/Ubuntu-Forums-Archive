---
title: "Killed my GUI"
date: 2007-12-03
forum: General Help
---

### Post by Windux525 on 2007-12-03
This was stupid on my part, but please bear with me.  Basically, the newest version of Gutsy kills my video input on boot, so I decided that I would upgrade my graphics card driver.  I, newbie that I am, read that I should uninstall my current driver and made the mistake here.  My mistake: I disabled my graphics card driver instead.  See the problem with this is, I don't know how to turn it back on again without my GUI.  Can you give me instructions as to how I can turn it back on via command line?

---

### Post by -grubby on 2007-12-03
reboot to recovery mode, type (short version, only asks about video) ```
sudo dpkg-reconfigure -phigh xserver-xorg
```  or longer version ```
sudo dpkg-reconfigure xserver-xorg
```

with either one, choose the correct driver, and off you go. It doesn't matter which one you use the first one just gives you the video questions only while the other (2nd) asks things like: keyboard,mouse, etc..

---

### Post by Windux525 on 2007-12-03
Thank you very much.

---

