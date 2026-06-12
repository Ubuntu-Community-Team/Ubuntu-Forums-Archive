---
title: "vmware error"
date: 2007-03-09
forum: General Help
---

### Post by nacr on 2007-03-09
Hello i am in need of help ... i was installing a vmware, but its always giving me a error that is :

A previous installation of VMware software has been detected.

Failure

Execution aborted.

So i do not now what i should do can you help me ?? Please !!!

---

### Post by zvacet on 2007-03-09
Uninstall all vmware files.Good place to start is etc.Delete vmware folder there and just chek in usr/bin,tmp,home(including hidden files)...If you anywere find more vmware files delete them.When you are sure that you don´t have any vmware file try to install again.

---

### Post by PriceChild on 2007-03-09
I don't recommend you doing it manually.
```
sudo apt-get remove vmware*
sudo vmware-remove.pl
```

---

