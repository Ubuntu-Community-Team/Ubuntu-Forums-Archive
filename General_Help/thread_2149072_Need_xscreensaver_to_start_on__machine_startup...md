---
title: "Need xscreensaver to start on  machine startup.."
date: 2013-05-27
forum: General Help
---

### Post by candtalan on 2013-05-27
How to arrange for xscreensaver to start automatically (when appropriate) when the machine is turned on?
iirc there was an app such as startup manager  I once used, is there something now please?

tia

---

### Post by ajgreeny on 2013-05-27
In your **startup-applications** list, which I assume still exists in unity, add an application with command ```
xscreensaver -no-splash
```
See [http://askubuntu.com/questions/48321/how-do-i-start-applications-automatically-on-login](http://askubuntu.com/questions/48321/how-do-i-start-applications-automatically-on-login)

---

### Post by candtalan on 2013-05-29
thanks! much appreciated.

---

