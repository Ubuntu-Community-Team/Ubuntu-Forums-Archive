---
title: "LTSP - Screen Lock"
date: 2013-05-17
forum: General Help
---

### Post by infringer on 2013-05-17
Generic LTSP setup on Ubuntu 12.04.2

I want to enable screen lock for one users.  I found the gsettings command to enable screen lock.  However, when the screen is locked, and the user enters their valid password.  The system responds with "incorrect password" and they cannot unlock the screen.

I've found several threads/web pages about screen lock and incorrect password, from incorrect owner to incorrect permissions, to deleting .Xauthority & .xsession_errors files.  Nothing seems to work.

Any suggestions on what to try next?

---

### Post by ipeters61 on 2013-05-17
Is it possible that the screen locker uses its own password, separate from the user's password?  I know back when I used Debian Testing and XFCE, playing around with different screen lockers, some lockers would use their own passwords.

Do you know which screen locker you are using?  There may/should be an option to have it sync passwords with the user passwords.

---

### Post by infringer on 2013-05-17
I'm not sure what screen lock program I'm using.  It's just the default screen lock found in System Settings > Brightness & Lock

---

