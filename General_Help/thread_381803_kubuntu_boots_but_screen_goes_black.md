---
title: "kubuntu boots but screen goes black"
date: 2007-03-11
forum: General Help
---

### Post by sjlyon5 on 2007-03-11
Hello,

I'm experiencing a problem when my Kubuntu system boots up.  it will run through the boot sequence fine but when it gets to the login screen after a few seconds maybe 5, the system blinks out and the screen goes black.  I've rebooted using a live CD and it worked fine.  I recently had a power outage but the system came back ok except for the wireless network card, but it ran fine.  I don't want to have to reinstall.  Also if anyone knows how to copy email contact list from the hard drive to a cd i would appreciate it.

Thanks
Stacey

---

### Post by zvacet on 2007-03-11
Ctrl+alt+F1
```
sudo /etc/init.d/kdm start
```
If this failed than 
```
sudo dpkg-reconfigure xserver-xorg
```
Export your contacts to Desktop(or in any other folder or directory),and you will see file with your contacts.Burn that file to Cd.

---

