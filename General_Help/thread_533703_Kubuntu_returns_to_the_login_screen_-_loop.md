---
title: "Kubuntu returns to the login screen - loop"
date: 2007-08-24
forum: General Help
---

### Post by LeGollemux on 2007-08-24
Hi, this has happened out of the blue. I start up one of my Kubuntu machines.. It loads the Xwindow login screen. I enter the password and the screen goes black. 

then returns to the login screen again. no error message. If I select console login, it works no problem. I can log in.

I have replaced the xorg.conf file with a stable backup version..still no luck. any ideas??

---

### Post by por100pre1 on 2007-08-24
Try reconfiguring the login screen:

```
sudo dpkg-reconfigure kdm
```

---

### Post by LeGollemux on 2007-08-24
Brilliant!! that worked perfectly.

Thank you..

---

