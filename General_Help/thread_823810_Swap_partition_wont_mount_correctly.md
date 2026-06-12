---
title: "Swap partition wont mount correctly"
date: 2008-06-09
forum: General Help
---

### Post by Ender305 on 2008-06-09
I don't think my Swap partition mounts correctly on startup.  I have an encrypted swap partition and an encrypted /home partition, it asks me for the passwords for both during startup, but last time I rebooted, the prompt was different for the swap password and there was some sort of error that flashed across the screen.  When I go into the system monitor, it says none of the swap is being used.  First I need a way to test if there really is a problem, and if there is, I need to know what to do.

---

### Post by Kevbert on 2008-06-09
If you enter
```
free -m
```
in terminal you should get the swap file in Megabytes (last figure).  To check if it's working just go to hibernate rather than shutting down.  Then restart the machine and the system should come up very quickly meaning the swap is working.

---

