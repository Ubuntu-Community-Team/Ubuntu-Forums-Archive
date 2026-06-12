---
title: "xserver crashes during startup"
date: 2006-08-22
forum: General Help
---

### Post by cptjaben on 2006-08-22
yesterday i downloaded an update relating to x.org i believe(wasn't too concerned about it at the time). today when i rebooted, i got the message that my Xserver failed to start. the log says, "xserver fatal error: No screen found." Does anyone know how this can be fixed?

Thanks

---

### Post by ahaslam on 2006-08-22
There was a problem with the xorg update 10.3
You should be able to fix this now (update 10.4 is out) by entering in the command line:

[B]sudo aptitude update 
sudo aptitude dist-upgrade[/B]

Tony.

---

### Post by cptjaben on 2006-08-22
Thanks, the problem has been fixed

---

### Post by ahaslam on 2006-08-22
> **cptjaben said:**
> Thanks, the problem has been fixed

No worries mate, I was also caught out ;)

Tony.

---

### Post by compwiz18 on 2006-08-22
See this thread if you have any more questions:
[http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)

---

