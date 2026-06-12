---
title: "How to stop Gnome from loading"
date: 2007-02-27
forum: General Help
---

### Post by Valiante on 2007-02-27
Sorry if this has been asked & answered before but I've tried searching and being new to Ubuntu (and Linux in general) I'm not sure of the right search terms to use and I'm not getting anywhere.

Basically I've built myself a box on which I'm going to run a web & mail server.  It's going to be administered remotely so I've found myself no longer needing the Gnome GUI.

All I want it to do is boot up to console - nothing fancy - just so it starts the relevant servers and doesn't load too much into memory.  Any help will be most useful!!!

Thanks in advance.

Valiante
A true Ubuntu n00b

---

### Post by Ramses de Norre on 2007-02-27
```
sudo aptitude install sysv-rc-conf
sudo sysv-rc-conf
```
Use the arrows to go down to "gdm" and unselect it for runlevel (column) 2 (the others are optional, you wont boot to them unless specifically specified).
GDM (the login manager) wont start on startup no more now, and thus neither will X.
To start it occasionally: ```
sudo /etc/init.d/gdm start
```

---

### Post by Valiante on 2007-03-01
That's great - thanks for your help!! :)

---

