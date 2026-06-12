---
title: "cron and gui apps"
date: 2007-04-08
forum: General Help
---

### Post by jordilin on 2007-04-08
I've added the following job to cron being root:
```
*/1 * * * * export DISPLAY=:0.0 && /usr/bin/gedit
```

gedit should come up every 1 minute, but it doesn't.
Anyone can explain why? :confused:

---

### Post by jordilin on 2007-04-08
Solved, the solution is that you have to provide the following command 
```
xhost +
```
so, cron can launch GUI apps. If you do not provide access by means of xhost, your program will not be launched.
xhost is the server access control program for X.
:guitar:

---

