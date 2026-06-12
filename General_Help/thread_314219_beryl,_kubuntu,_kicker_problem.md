---
title: "beryl, kubuntu, kicker problem"
date: 2006-12-07
forum: General Help
---

### Post by vranikx on 2006-12-07
hello all, 

i have kubuntu edgy eft and beryl installed and have little problem. 
every time when i start kubuntu autostart programs loaded but no into kicker. Look at the screenshot. What i must do for put these programs into kicker? 

[[IMG]http://img353.imageshack.us/img353/5011/desktopnn7.th.jpg[/IMG]](http://img353.imageshack.us/my.php?image=desktopnn7.jpg)

thanx for your helps...and sorry for my english

---

### Post by bantu on 2006-12-18
Start beryl with a delay (about 8 seconds) that'll give the progs time to start before beryl is fired up...

---

### Post by vranikx on 2006-12-18
> **bantu said:**
> Start beryl with a delay (about 8 seconds) that'll give the progs time to start before beryl is fired up...

ok, but how can i start beryl with this delay?

---

### Post by zvoase on 2007-07-04
If you have a script which automatically loads beryl for you on startup, then the command "sleep" will pause execution of the next command for a specified number of seconds. For example, place the following code in ~/.kde/Autostart/beryl.sh:
```

#!/bin/bash
sleep 8
beryl --replace || kwin 
```
This will also make sure that, should beryl crash, kwin will be started. Alternatively, you could use beryl-manager.

---

