---
title: "apache not uninstalling"
date: 2006-11-15
forum: General Help
---

### Post by xyrer on 2006-11-15
Hi, i installed ubuntu on a small 400mhz and installed apache but didn't got php to work well, so i removed it  and tried to install apache2, but apache2 never worked at all and apache folders and configurations are still there, am i doing something wrong or is it that aptitude doesn't fully uninstall apache? i removed apache2 and the same happened, i find package management very bad in ubuntu as it should have been removed.
Any way to revert my ubuntu back to the way it was before installing apache in the first place?

---

### Post by jimbren on 2006-11-15
If you look in /etc/init.d, you'll probably find that apach2 isn't there, and thus isn't installed.

If you want to remove any trace of apache2, then do this:
```
sudo apt-get remove --purge apache2
```

This will remove all folders and config files.

---

### Post by lamego on 2006-11-15
If you don't use the purge option the configuration files are not deleted, thats the expected behavior for any .deb package so that you can reinstall the application or simply upgrade without losing the configuration.

---

### Post by xyrer on 2006-11-15
I see, didn't know that option. Anyway i used synaptic for that, but then i have another question, apache2 is not an upgrade to apache? i say it because i removed apache and then installed apache2 but it didn't work, in any way, why doesn't it work if apache was supposed to be uninstalled?

---

