---
title: "Autostart a process/app Feisty"
date: 2007-10-16
forum: General Help
---

### Post by Hopworks on 2007-10-16
I see a few threads on this, but not Gnome and Ubuntu Feisty. 

Forgive my noobness, but I want to have hellanzb start up in daemon mode when the system boots up, even before logging into gnome. How can I do that?

I did a find -name autostart* and found a few locations...
```
./usr/share/gnome/autostart
./usr/share/autostart
```

Is it just a matter of putting in a file with "hellanzb -D" in it? Which folder?

I wanted to ask before experimenting. I don't want to hose my stable machine.

Thanks!
Hop

---

### Post by wormser on 2007-10-16
The start up location is /etc/init.d/.  I have only removed things from starting up here and do not know the details on what is needed to be done.  Sorry I could not help you further but this [link]("http://www.debian-administration.org/articles/28") should help you.

---

