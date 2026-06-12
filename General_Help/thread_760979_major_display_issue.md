---
title: "major display issue"
date: 2008-04-20
forum: General Help
---

### Post by csulok on 2008-04-20
hey

i'm testing ubuntu hardy since alpha 5 and i restart regularly, like every week. after today's restart i noticed dead pixels on my screen, which at first i thought were dead pixels on my lcd monitor, however i found out that they persist through screenshots (!) so they are not related to my lcd monitor.

they disappear and reappear after a second if i move a window over them, or if i minimize and maximize a window they disappear totally. when scrolling down in firefox, i can see them create lines! in pidgin it's really really bad, if i move around a window for ~15 seconds this is the result:

[http://grip-system.hu/stuff/asdasdasd.png](http://grip-system.hu/stuff/asdasdasd.png)

again, this is a screenshot.

i'm thinking there is a serious memory corruption in the videocard but i could be totally wrong. some info:

[sudo nvclock -i]("http://grip-system.hu/stuff/nvclock.txt")
[dmesg]("http://grip-system.hu/stuff/dmesg.txt")
[dpkg -l]("http://grip-system.hu/stuff/dpkg-l.txt")
[sensors]("http://grip-system.hu/stuff/sensors.txt")

how would i go about diagnosing this serious issue? what other information do i need to make bug reports and stuff?

thank you

---

