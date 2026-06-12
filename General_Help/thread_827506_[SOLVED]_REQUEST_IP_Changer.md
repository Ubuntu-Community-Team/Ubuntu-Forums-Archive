---
title: "[SOLVED] REQUEST IP Changer"
date: 2008-06-12
forum: General Help
---

### Post by xMoDx on 2008-06-12
Hello,

Does anyone know where i can get an ip changer? i have static ip setup at home and at work have also different setup of static ip, i would like to know if there is same functions like, [http://www.netsetman.com/](http://www.netsetman.com/) "in windows" but in Ubuntu....

---

### Post by sdennie on 2008-06-12
You should be able to do something like this by left clicking on the network manager icon (by default in the top panel on the right).  Clicking Manual Configuration should give you a dialog that allows you setup profiles, static IPs, etc.

---

### Post by xMoDx on 2008-06-13
Yes this perfectly work thanks,

under the location TAB after i click Network Icon, 

set ip settings and save location

note: make sure you restart network if you change settings

code: sudo /etc/init.d/networking restart

---

