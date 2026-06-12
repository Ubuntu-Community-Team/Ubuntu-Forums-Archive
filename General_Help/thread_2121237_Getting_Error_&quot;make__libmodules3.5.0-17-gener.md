---
title: "Getting Error &quot;make: *** /lib/modules/3.5.0-17-generic/build: No such file &quot;"
date: 2013-03-01
forum: General Help
---

### Post by gireeshkkm on 2013-03-01
I was trying to install mblaze application in my ubuntu gnome remix 12.10
But I am getting following error

[FONT=verdana]make -C /lib/modules/3.5.0-17-generic/build M=/usr/local/bin/ztemtApp/zteusbserial/below2.6.27 modules
make: *** /lib/modules/3.5.0-17-generic/build: No such file or directory.  Stop.
make: *** [modules] Error 2
[/FONT]
Please help me to fix this...

---

### Post by steeldriver on 2013-03-01
Did you install the appropriate kernel headers for your system?

```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by gireeshkkm on 2013-03-01
Thanks steeldriver
Its worked.

---

