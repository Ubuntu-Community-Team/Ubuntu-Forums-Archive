---
title: "autostart firefox"
date: 2007-11-17
forum: General Help
---

### Post by filo1234 on 2007-11-17
Hi guys i need an aid, i explain my problem: i making an ubuntu custom with UCK , i need to know how to start firefox on boot ...i need to know the path where i can put /usr/bin/firefox ...on kubuntu there is a path Autostart on ~.kde  but in ubuntu where is this path? thank you

---

### Post by taurus on 2007-11-17
You mean you want firefox to start when you log into Gnome!

System -> Preferences -> Sessions

---

### Post by filo1234 on 2007-11-18
So i want to stratup firefox automatically, but i cannot make this  from System.preferences-themes. I must make it from command line and i don' t know where is path autostart on ubuntu.  On kubuntu i put a little script
```
#!/bin/sh
/usr/bin/firefox
exit0 
```
in path ~.kde/Autostart   but in ubuntu i not found a similar path ...I must to make this work from command line because i creatind an ubuntu custom with UCK .
Thanks

---

### Post by bollix47 on 2007-11-18
~/.config/autostart

---

### Post by filo1234 on 2007-11-18
there isn' t autostrat on .config   !!!!   maybe because i have gutsy ? where i can put that script?  maybe in some path /etc/init.d and so on??

---

