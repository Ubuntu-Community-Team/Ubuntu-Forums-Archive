---
title: "vnc gives blank grey screen"
date: 2007-03-22
forum: General Help
---

### Post by voipfc on 2007-03-22
I have tried to install vnc on dapper drake according to this howto - [http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402).

But whenever I try to start VNC I get a blank grey screen

What am I missing?

---

### Post by bibulle on 2007-04-07
**I got it !!!**

Just add "DisallowTCP=false" to file "/etc/gdm/gdm.conf-custom" .....
 and it works !!!

---

