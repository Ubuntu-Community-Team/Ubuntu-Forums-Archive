---
title: "[SOLVED] Why does date display utc?"
date: 2008-05-23
forum: General Help
---

### Post by cmnorton on 2008-05-23
My clock application (KDE) displays the correct local time. The bash date command displays the UTC time. Set date and time automatically is set in Configure KDE Control module. What do I need to change to see the correct time in bash?

Edit:
------------------------------------------
Solution worked like a champ.

[http://ubuntuforums.org/showthread.php?t=135214](http://ubuntuforums.org/showthread.php?t=135214)

specifically,  sudo  ln  -s  -f  /usr/share/zoneinfo/America/New_York  /etc/localtime

---

