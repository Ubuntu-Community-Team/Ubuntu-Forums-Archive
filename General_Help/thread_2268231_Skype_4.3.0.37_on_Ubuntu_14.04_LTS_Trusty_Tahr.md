---
title: "Skype 4.3.0.37 on Ubuntu 14.04 LTS Trusty Tahr"
date: 2015-03-07
forum: General Help
---

### Post by mdavis1231 on 2015-03-07
It seems like quite a bit whenever I start up my laptop, and my Skype loads, the system tray icon will appear at first, then disappear and I get the bloack box with the red circle in it.  I have to quit my Skype, then start it up again to get the Skype system tray icon.  Is there maybe a package that I'm missing somewhere, are there other people experiencing this besides just me, or what?

---

### Post by ajgreeny on 2015-03-07
Add a sleep period to your skype autostart command eg
```
bash -c "sleep 30; skype"
```That will probably work for you.

---

### Post by Bucky Ball on 2015-03-07
*Thread moved to **General Help**.*

Please note the description of the ***New to Ubuntu*** sub-forum:

> The perfect place to post for your Ubuntu support if you are new to Linux.

Thanks.

---

