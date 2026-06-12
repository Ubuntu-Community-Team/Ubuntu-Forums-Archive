---
title: "Need help getting old LightDM back"
date: 2013-11-20
forum: General Help
---

### Post by crazymonkey05 on 2013-11-20
ok so i installed Kubuntu over stock ubuntu 13.10 and decided to migrate back to stock ubuntu 13.10 but the only problem i have is that KDE set my lightDM to KDM and i cant change it back to stock. now when i say cant its really like KDE replaced lightDM with its own and now i have two lightDM and both are KDE login managers and im not a big fan of it. so any help will be great thanks

---

### Post by ibjsb4 on 2013-11-21
```
sudo dpkg-reconfigure lightdm
sudo /etc/init.d/lightdm start
```

See if that will do any good :)

---

### Post by crazymonkey05 on 2013-11-21
nope still at kdm. this is really getting annoying:mad:

---

### Post by ibjsb4 on 2013-11-22
Check  /etc/X11/default-display-manager

[http://ubuntuforums.org/showthread.php?t=2171542&p=12775018#post12775018](http://ubuntuforums.org/showthread.php?t=2171542&p=12775018#post12775018)

---

### Post by crazymonkey05 on 2013-11-23
ok im sorry for being such a noob. after a lot of editing i got it back. what i was looking to change was the greeter not the DM so i finally fixed it by doing these steps.

1) ```
gksu gedit /etc/lightdm/lightdm.config
```

2)edited ```
greeter-session=kde-plasma
``` to ```
greeter-session=unity-greeter
```

and wala its all back to normal.

thanks again guys i'll mark thread as solved

---

