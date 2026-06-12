---
title: "help gutsy network connections not working after software uninstall"
date: 2008-06-24
forum: General Help
---

### Post by exneo002 on 2008-06-24
I uninstalled some software via add remove on my gutsy box and now my internet connection doesnt work. All my hardware worked before. Are their commands I can run to reconfigure my network or scan for my ethernet connection please this problem is urgent.

---

### Post by ryanhaigh on 2008-06-27
```
sudo dhclient eth0
```
That should get you an IP for your wired network card assuming your network uses dhcp.

If you need some more help please explain how you connect to the net ussually.

---

