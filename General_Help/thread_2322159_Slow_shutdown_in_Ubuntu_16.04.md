---
title: "Slow shutdown in Ubuntu 16.04"
date: 2016-04-26
forum: General Help
---

### Post by maikcrew-seznam on 2016-04-26
Hello,

   I try new Ubuntu 16.04 with Unity. When I turn off the PC.  Shows me countdown for stop jobs (A stop job is running for Sesssion c...ser destop 1 minutes and 30 second). You do not know how someone please stop this annoying deduction, please?

Michal

---

### Post by charles-noneman on 2016-04-28
sudo systemctl disable cups-browsed 


When you shutdown it will not be fixed. But every time after that shutdown will be back to normal.

---

### Post by maikcrew-seznam on 2016-04-30
Thanks. I am try your advice and looks that it is good solution :-) 

Before reading your answer I using command from Firefox autoshutdown addon dbus-send like shortcut with Cinnamon launcher. In Unity dbus-send command do not work only like sleep to RAM.

---

### Post by maikcrew-seznam on 2016-05-11
Maybe and seems that systemd is offender slow start and primary shutdown. It would install back init?

---

