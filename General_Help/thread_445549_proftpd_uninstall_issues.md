---
title: "proftpd uninstall issues"
date: 2007-05-16
forum: General Help
---

### Post by asus on 2007-05-16
I installed proftpd now i want to uninstall it, so i do a sudo apt-get remove proftpd .. .. it removes it as far as i can see, but when i go to reinstall it, it does not give me the config screen it had before that let me choose standalone or init.d

am i removing it wrong?  I dont have a GUI interface, i just use the plane server version of ubuntu.  

Thanks

---

### Post by nikhilk on 2007-05-16
Probably you want to try
```
sudo aptitude purge proftpd
```

---

### Post by asus on 2007-05-16
did you mean aptitude purge proftpd

anyway, that doesnt seam to work, the files still seam to be there.  ive tried apt-get remove and aptitude purge proftpd ect..

---

### Post by nikhilk on 2007-05-16
That is strange! aptitude purge removes the package as well as its config files from a system. It seems that the config files are still there even after a purge. So you can try manually removing the config file. I guess it is "/etc/proftpd.conf"

---

