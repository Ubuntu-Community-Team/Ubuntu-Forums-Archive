---
title: "Monitor out of sync durring splash"
date: 2008-02-04
forum: General Help
---

### Post by sargonious on 2008-02-04
My Sylvania L181 which is configured properly in xorg.conf for some reason is out of sync on the loading bar. I previously had a Dell CRT on my PC but I switched it in favor of an LCD. What settings do I configure to keep it from going out of sync durring the splash screen where it shows the loading bar. It does it when I exit the system as well.

---

### Post by ajgreeny on 2008-02-04
You need to look in /etc/usplash.conf and change the resolution figures to those for your monitor.  ```
gksudo gedit /etc/usplash.conf
``` will let you edit the file, but make sure you backup first.

---

