---
title: "[SOLVED] Completly remove Google Earth from .bin installation"
date: 2008-07-08
forum: General Help
---

### Post by pi.boy.travis on 2008-07-08
I recently uninstalled Google Earth by removing it's directories from /usr/google-earth .  I know that there must be some other portion of it left behind, because it is still in my applications menu.  I have checked /usr/bin  ,  /usr/sbin  ,  and /usr/local  and my home directory for any remaining files, but found none.  

Where are they. . . ? :confused:

Thanks!

---

### Post by iaculallad on 2008-07-08
Had you tried:

```
cd /opt/google-earth
sudo ./uninstall
```

and try removing the data folder in you home directory:

```
sudo rm -rf ~/.google-earth
```

---

### Post by pi.boy.travis on 2008-07-08
Thanks!  Those are the ones I couldn't find.

For anyone else who uses this, here are some others:

/usr/local/share/applications

/usr/share/applnk

/usr/local/share/mime/packages

Be sure to check "Show hidden files" in the view menu.

---

