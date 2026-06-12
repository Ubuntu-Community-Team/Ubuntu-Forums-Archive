---
title: "updation prob"
date: 2017-12-11
forum: General Help
---

### Post by pushpa2 on 2017-12-11
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

---

### Post by yancek on 2017-12-11
If you have the Software Manager open and then use apt-get or use either twice you will get that error.  Close everything down and reboot and try again and see what you get.
It would also be useful to indicate which release of Ubuntu you are using.

---

### Post by Frogs Hair on 2017-12-11
Close all update applications and try the following commands.

```
sudo fuser -vki /var/lib/dpkg/lock; sudo dpkg --configure -a

```
```
sudo apt update
```

```
sudo apt upgrade
```

---

### Post by deadflowr on 2017-12-11
It could be unattended-upgrades running.
In which case, let it run and then all updates (or at least security updates) should be installed and applied.
You can check with top and see if either unattended-upgrades or dpkg is running.

---

