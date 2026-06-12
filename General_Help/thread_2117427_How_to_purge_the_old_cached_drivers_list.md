---
title: "How to purge the old cached drivers list?"
date: 2013-02-18
forum: General Help
---

### Post by nodnolse1 on 2013-02-18
Hi, time a go I added few repositories that offered drivers update. I removed them from my sources list but I still have them in 'Additional Drivers' section (System settings/Hardware/Additional Drivers). Now I have only the default Ubuntu official repositories and I'd like to remove all the leftovers created from ppa's like 'oibaf', 'ubuntu-x-swat' and others. Please have a look to the screenshot to understand what I mean. Thanks for reading, Paolo

Ps: I already run 'sudo apt-get update|install -f|autoremove|autoclean|dist-upgrade|upgrade', dpkg --configure -a' and rebooted many times.

---

### Post by MrsUser on 2013-02-18
I guess you can do that conveniently with Bleachbit. The menu item is "APT" or via Terminal:

```
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get autoclean
```

---

