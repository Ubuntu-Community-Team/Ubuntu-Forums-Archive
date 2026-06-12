---
title: "Set visual effects to none"
date: 2008-05-13
forum: General Help
---

### Post by AntiHeroJoe on 2008-05-13
I'm having a bit of trouble keeping visual effects off. I set visual effects to 'none', but when I restart, it puts the setting back to 'normal'. I guess Ubuntu doesn't believe I want to disable wobbly windows and a spinning cube! Any help would be appreciated, this is just an annoyance each time I have to restart. Thanks! =)

---

### Post by cubeist on 2008-05-13
One way is to use alt+f2 and type "metacity --replace" If this doesn't work at reboot, add it to your sessions list, or...
you could probably go into synaptic and uninstall compiz and compiz plugins if you plan to never use it!

---

### Post by tommyhakinen on 2008-05-14
Install Fusion-Icon
> sudo apt-get install fusion-icon

Access it from System Tools > Compiz Fusion Icon
On the Notification Area, right click on the Compiz Fusion Icon and switch the Windows Manager to Metacity (No visual effect)

---

### Post by korin43 on 2008-05-14
sudo apt-get remove compiz should do it

---

