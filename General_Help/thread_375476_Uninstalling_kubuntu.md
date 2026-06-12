---
title: "Uninstalling kubuntu"
date: 2007-03-03
forum: General Help
---

### Post by nixfreak on 2007-03-03
After getting errors while trying to install kubuntu i finally decided to uninstall it, i used the methos posted in this post [http://ubuntuforums.org/showthread.php?t=354155&highlight=kubuntu-artwork-usplash](http://ubuntuforums.org/showthread.php?t=354155&highlight=kubuntu-artwork-usplash)

i posted the error i was getting here: [http://ubuntuforums.org/showthread.php?t=375072&highlight=kubuntu-artwork-usplash](http://ubuntuforums.org/showthread.php?t=375072&highlight=kubuntu-artwork-usplash)

but it wouldnt even unintall :(

i get this error message:


```
Cannot find /lib/modules/2.6.15-23-server
dpkg: error processing usplash (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 usplash
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up usplash (0.2-4) ...
Cannot find /lib/modules/2.6.15-23-server
dpkg: error processing usplash (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 usplash

```

plz help

nixFreak

---

### Post by rkrug on 2007-03-03
```
sudo apt-get remove kubuntu-desktop
```

try that^

---

### Post by rkrug on 2007-03-03
or you could try the really long code you tried already without:

```
kubuntu-artwork-usplash
```

---

