---
title: "Updating Errors"
date: 2007-12-24
forum: General Help
---

### Post by MantinoX on 2007-12-24
Hello I'm having problems getting the daily update for ubuntu 
Im presented with this screen stating:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When I do so in the terminal is asks

dpkg: requested operation requires superuser privilege

What should I do? Im quite new to this program.

Thanks

---

### Post by taurus on 2007-12-24
```
**sudo** dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by MantinoX on 2007-12-24
Works thank you! 	\\:D/

---

