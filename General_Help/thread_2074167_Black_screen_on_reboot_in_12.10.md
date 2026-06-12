---
title: "Black screen on reboot in 12.10"
date: 2012-10-21
forum: General Help
---

### Post by Szor3n on 2012-10-21
I'm not quite sure what's causing it, but whenever I reboot instead of the login screen, I've got a black screen with the mouse cursor.  If I hit ctrl alt f2 I can login, delete .Xauthority and change my home folder ownership to my account.  If I do these things, next time I shut down all the way and then boot up, it loads properly. I'm running 12.10 from a clean install.  This is a really annoying issue, if anyone can help it would be greatly appreciated!

---

### Post by DarknessKight on 2012-10-29
I have this same issue. Going to tty and restarting lightdm makes it appear again for me.

---

### Post by Szor3n on 2012-11-03
Restarting lightdm fixes it for me too.  There is a bug on Launchpad, and it seems to be related to people who have SSD's.

[bug page]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1066410")

---

