---
title: "broken package, won't let me remove/reinstall"
date: 2008-05-24
forum: General Help
---

### Post by samosamo on 2008-05-24
i tried installing webmin-slbackup yesterday but something got messed up, so i installed it from the developer's website with no problems.  but now every time i use aptitude, it complains about this error.  i tried removing webmin-slbackup from apt but it gives this error also.

> sean@santo:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up webmin-slbackup (0.0.9-1) ...
/var/lib/dpkg/info/webmin-slbackup.postinst: 4: /usr/sbin/update-webmin: not found
dpkg: error processing webmin-slbackup (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 webmin-slbackup
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by bwhite82 on 2008-05-24
Try:

> sudo apt-get -f install

---

### Post by samosamo on 2008-05-24
no sir, same error.  keeps looking for /usr/bin/update-webmin, an app which is nowhere on my system.. even with a working install of webmin

---

### Post by drs305 on 2008-05-24
Open up /var/lib/dpkg/info/webmin-slbackup.postinst and see what would happen if you just comment out what I would guess would be line 4 where it references /usr/sbin/update-webmin. Or you could rename the file to at least temporarily regain aptitude. My guess is that you could also just make a backup, delete the file, regain synaptic, and then reinstall the app again.

---

### Post by samosamo on 2008-05-26
thank you!  that worked.  i had to comment out another line in another file too. someone should update this package

---

