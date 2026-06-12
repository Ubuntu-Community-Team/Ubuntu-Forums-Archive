---
title: "X Server Broken"
date: 2006-10-30
forum: General Help
---

### Post by pattymnaish on 2006-10-30
After (unsuccessfully) attempting to install my Netgear Wireless USB connector on Ubuntu 6.10, I restarted to find that the X server was broken. I just got a black screen where I could type, but not anything else. Why has this happened? I have not modified any system files except for the driver blacklist (I added a few interfering wireless drivers).
 Also, how do I fix this? I don't mind if I have to re-install, but I'd rather not. :???:

---

### Post by pattymnaish on 2006-10-30
I'm running a Dell Dimension 2400, 256MB RAM, 2.8Ghz Pentium IV processor.

---

### Post by slimdog360 on 2006-10-30
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by pattymnaish on 2006-10-30
I'm afraid that hasn't helped. I think I'm just gonna go ahead and re-install. I've only used it for one day, anyway.

---

