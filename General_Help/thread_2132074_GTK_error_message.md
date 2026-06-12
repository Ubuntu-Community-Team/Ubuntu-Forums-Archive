---
title: "GTK error message"
date: 2013-04-03
forum: General Help
---

### Post by cmcanulty on 2013-04-03
I get the following error yet the command worked OK but it says critical error, can someone explain how to fix? 

```
cmcanulty@darcytech:~$ exo-preferred-applications

(exo-helper-1:3744): Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed
cmcanulty@darcytech:~$ 

```

---

### Post by 3rdalbum on 2013-04-03
Don't worry about it. GTK throws up many warning messages, they are only for developers and even developers can mostly ignore them. If the program works fine that's all the matters.

---

### Post by Frogs Hair on 2013-04-03
I found two bugs reports related to Thunar . The following is the closest match .[https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1082193](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1082193)

---

### Post by cmcanulty on 2013-04-04
Ok thanks, I thought critical should mean, get worried

---

