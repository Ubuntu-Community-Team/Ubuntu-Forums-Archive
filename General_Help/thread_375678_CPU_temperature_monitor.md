---
title: "CPU temperature monitor?"
date: 2007-03-04
forum: General Help
---

### Post by SnowPunk98 on 2007-03-04
Is there a good CPU temperature monitor I can use for my Dell E1705?

---

### Post by taurus on 2007-03-04
I think you are talking about lm-sensors here.

[http://www.lm-sensors.org/](http://www.lm-sensors.org/)

---

### Post by Redeyes_Gambit on 2007-03-04
If you want a nice front-end to that, try Sensors Applet.

Do:



sudo apt-get install sensors-applet



Now restart (there is probably a command to refresh the applet list but I don't know it)

Finally right-click on your gnome-panel, hit add to panel, and select the sensor applet. Easy as pie!

---

### Post by Xbehave on 2007-03-12
and for kde theres ksensors

---

