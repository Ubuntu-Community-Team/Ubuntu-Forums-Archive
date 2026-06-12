---
title: "webmin won't show updated cpu information"
date: 2013-03-03
forum: General Help
---

### Post by cybercity@localhost on 2013-03-03
Hi all,

I've recently upgraded my cpu from core 2 duo to Xeon Quad processor. everything is fine but webmin still shows my old cpu and memroy configuration. i have tried dpkg-reconfigure webmin but nothing happens. is there another method to tell webmin to update cpu information?

---

### Post by cybercity@localhost on 2013-03-03
i have solved the problem. if somebody else has the same problem they could also fix this by adding a line /proc in webmin configuration --> Operating system and environment ---> program search path. :)

[CENTER][IMG]http://i48.tinypic.com/334kgzr.png[/IMG]
[/CENTER]

---

