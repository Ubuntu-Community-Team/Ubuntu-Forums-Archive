---
title: "APT logging"
date: 2008-03-22
forum: General Help
---

### Post by 1010011010 on 2008-03-22
I would like to know if there is anyway to log installations with APT.  I already know about /var/log/dpkg.log, but there is not enough information.  

For instance, if I install firefox, the executable is put in /usr/bin/firefox, the configuration files are in /etc/firefox/, the libraries are in /usr/lib/firefox, an so on.  When I install a package, I would like to be able to look at a log file, or something else, and see exactly what was installed, where it was installed, and where the config files are, etc.  In other words, I would like to be able to see all files that a new installation has made.  I know about slocate, but I would like to log the actual installation process.

Thanks.

---

### Post by pointone on 2008-03-22
```
dpkg --listfiles <package>
```

---

