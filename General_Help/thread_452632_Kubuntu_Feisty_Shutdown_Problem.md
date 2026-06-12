---
title: "Kubuntu Feisty Shutdown Problem"
date: 2007-05-23
forum: General Help
---

### Post by cyrusrayne on 2007-05-23
I've been trying both Ubuntu and Kubuntu for a while now, and I'm noticing a problem with Kubuntu that I never did with Ubuntu.  Whenever I try to shut down, it'll go to a blank screen and sit there.  I'll leave it for five to ten minutes and it'll still be there.  When I try to make my computer shut off it'll run fsck when I boot back up, which would probably be a sign that it wasn't doing anything at all.  Again, I've been using Ubuntu Feisty as well but it hasn't duplicated the problem.

---

### Post by garich on 2007-05-28
Same problem here. When I choose the "Shut Down" option from the Log Out menu in Kubuntu, everything goes fine till the turn off of the monitor. It turns off but the computer still continue working. What might be the solution?

---

### Post by eggdeng on 2007-05-28
Try adding ```
apm power_off=1
``` to the /etc/modules file. This fix is from [http://ubuntuforums.org/showthread.php?t=290713](http://ubuntuforums.org/showthread.php?t=290713).

---

