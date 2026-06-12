---
title: "Frozen Mouse after Boot (temp)"
date: 2015-05-09
forum: General Help
---

### Post by Quarkrad on 2015-05-09
I recently had to install win7 on the first partition of my HD (clean install over winxp).  This wiped out GRUB so I reinstalled (it) using the boot CD - I've had a lot of success with this boot CD.  My main system is 14.04 in gnome classic mode.  What is happening is that when the Desktop boots the top panel is a different colour to normal and the mouse is frozen - after about 10 secs the top panel changes to it's normal colour and the mouse is free is operate normally.  I do not know what is happening but another description could be that the theme is not loaded straight away (e.g. the colour of the top panel) and after about 10secs is configures itself and the mouse is free.  I could be wrong re the theme (probably am) - any advise appreciated.

---

### Post by Quarkrad on 2015-08-13
It's started again, after a few months of behaving normally.  Actually, I do not think the problem is the mouse - what happens is the whole Desktop freezes for about 43secs and then becomes available/active.   Specifically - after the Desktop initially appears - everything is frozen, then after the 40-45secs the icons in the top panel appear to reset themselves and change to a different set; the mouse is active and I'm away.   I normally use gnome-fallback desktop but this freezing happens if I switch to the Unity Desktop.   I have tried changing my Desktop theme to default but I still get the freezing. Any advice appreciated.

---

### Post by Quarkrad on 2015-08-13
Is there a log in /var/log that I can clear and then use to see what is happening?

---

### Post by Quarkrad on 2015-08-15
bump

---

### Post by Quarkrad on 2015-08-15
I have solved this - it was one of two usb cards I had attached to my pc, disconnecting them has solved the problem.  However, why did it suddenly appear again after 4 months - strange.

---

