---
title: "Low graphics mode"
date: 2012-12-12
forum: General Help
---

### Post by Code9 on 2012-12-12
I installed Ubuntu 12.10 on my laptop. The display was working, but I decided to install the Nvidia drivers in order to get Google Earth to work. Now on reboot it is telling me that it's running in low graphics mode. There is no mouse and the system seems to freeze and I can't progress past the second screen. Any help is appreciated.

---

### Post by Code9 on 2012-12-12
I solved this. My computer is a 2012 MacBook Pro 9,1. It doesn't have a Retina display, but has the dual GPU (Nvidia and Intel). I accidentally installed the Nvidia drivers when the computer was only detecting the Intel card.

I solved this by dropping into the root shell via the recovery menu and getting read/write access by running the following: 

```
mount --options remount,rw /
mount --all
``` 

This allowed me to run apt-get and remove the Nvidia drivers. 

```
apt-get remove --purge nvidia-current 
```

---

