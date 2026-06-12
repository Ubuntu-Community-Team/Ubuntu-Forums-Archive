---
title: "Reinstalling Ubuntu without loosing windows"
date: 2015-05-27
forum: General Help
---

### Post by ROVguy on 2015-05-27
Is it possible to reinstall Ubuntu 14.04 without touching windows on a dual boot? More importantly is it possible to use the live USB stick to repair Ubuntu to the way it was when it first installed without loosing any files?

Thanks

---

### Post by dino99 on 2015-05-27
if your data & settings are stored into a /home partition (not a home folder) then you are safe to reinstall (if you take care of not formatting /home indeed), otherwise do a backup
See the 'something else' option for manual reinstall

---

### Post by mattharris4 on 2015-05-28
In the reinstall I did recently on my desktop I had an option to reinstall (actually I installed Xubuntu in place of Edubuntu but it used the generic "Ubuntu" in its messages displayed on screen at that time) over the current "Ubuntu" install and not affect Windows XP.  I would select "install Ubuntu" on the first screen (where you would select either try or install) and see if you get that option on the install method selection screen.  If you get it you should be fine.  If not you haven't affected anything yet at that screen and you can decide what to do then.

Good luck.  I hope I have helped you.

---

### Post by ROVguy on 2015-05-28
Thanks for the suggestions. I was asking this as I messed up the grub component though I didn't know it was grub that i messed up. I just did a boot-repair and fixed the issue so I no longer have to do this.

---

