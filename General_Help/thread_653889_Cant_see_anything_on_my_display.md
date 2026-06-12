---
title: "Cant see anything on my display"
date: 2007-12-30
forum: General Help
---

### Post by WillThePlank on 2007-12-30
i was messing around trying to get dual monitors back and now i cant see anything when it loads the gui

i see everything upto login and nothing comes up on either monitor but the monitor stay on showing just black....what do i do?

---

### Post by foolsh on 2007-12-31
More details would help 
post your xorg.conf file so we can see what happened?
you could CTRL+ALT+F1 login then 
```
ls /etc/X11
```
and see if there are any extra xorg.conf files you could restore to a working configuration
like 
xorg.conf.1
xorg.conf.2
xorg.conf.20071227135515
if so
the xorg.conf.1 would be the first one your machine used
just 
```
sudo cp /etc/X11/xorg.conf.1 /etc/X11/xorg.conf
```
and reboot
```
sudo reboot
```

---

