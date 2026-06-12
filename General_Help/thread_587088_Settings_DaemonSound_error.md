---
title: "Settings Daemon/Sound error"
date: 2007-10-22
forum: General Help
---

### Post by LinuxNewb092 on 2007-10-22
The title says it all, please help me.
EDIT: I have just booted into my Windows Partition and I can hear everything fine. When I booted into Ubuntu after logging in I got "Cannot load GNOME Settings Daemon", whats wrong with Ubuntu?

---

### Post by Super TWiT on 2007-11-02
I had this problem too.  What ended up fixing it for me booting into the recovery kernel (which you can choose at startup) and typing once its all booted typing ```
gnome-settings-daemon
```  Even though it threw out an error, the next time I tried to log in everything was fine.  Hope this will work for you.  Seems like a lot of others are having this problem.

---

