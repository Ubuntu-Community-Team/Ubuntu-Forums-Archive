---
title: "Gnome doesn't work after memory upgrade"
date: 2007-10-24
forum: General Help
---

### Post by FunkyJack on 2007-10-24
After I inserted 512MB DDR memory my gnome won't start.
When it needs to show login screen after boot, it just turns off monitor.
Windows and Ubuntu recovery mode work fine and memory test shows no errors.

Can memory order in sockets cause this problems?
Before upgrade it was:
Socket1 - 256MB DDR
Socket2 - empty
Socket3 - 256MB DDR

Now it is:
Socket1 - 256MB DDR
Socket2 - 512MB DDR
Socket3 - 256MB DDR

---

### Post by FunkyJack on 2007-10-24
Problem solved after doing some xorg configuration changes :)

---

