---
title: "chown not working"
date: 2012-10-18
forum: General Help
---

### Post by bobman321123 on 2012-10-18
despite repeatedly running ```
sudo chown -Rv josh:josh /mnt/data
```
it still lists files in the directory as owned by root. Why is chown not working? 
The terminal outputs a massive string of working messages like this: 
```

changed ownership of `/mnt/data/Applications/redeclipse-1.3.1/src/game/client.cpp' from root:root to josh:josh
changed ownership of `/mnt/data/Applications/redeclipse-1.3.1/src/game/compass.h' from root:root to josh:josh
changed ownership of `/mnt/data/Applications/redeclipse-1.3.1/src/game/defend.cpp' from root:root to josh:josh
changed ownership of `/mnt/data/Applications/redeclipse-1.3.1/src/game/defend.h' from root:root to josh:josh
changed ownership of `/mnt/data/Applications/redeclipse-1.3.1/src/game/defendmode.h' from root:root to josh:josh
changed ownership of `/mnt/data/Applications/redeclipse-1.3.1/src/game/duelmut.h' from root:root to josh:josh
changed ownership of `/mnt/data/Applications/redeclipse-1.3.1/src/game/entities.cpp' from root:root to josh:josh
changed ownership of `/mnt/data/Applications/redeclipse-1.3.1/src/game/extinfo.h' from root:root to josh:josh
changed ownership of `/mnt/data/Applications/redeclipse-1.3.1/src/game/game.cpp'
```

---

### Post by nothingspecial on 2012-10-18
What file system is the mounted partition ?

---

### Post by bobman321123 on 2012-10-18
The filesystem is an ntfs one.

---

### Post by papibe on 2012-10-18
Hi bobman321123.

NTFS does not support neither ownership and Linux's permissions.

The way you work around that is using the proper setting on the mount options. There you can assign both fixed ownership and permissions.

Let us know how it goes.
Regards.

---

### Post by nothingspecial on 2012-10-18
Well ntfs doesn't support linux file permissions unless you specify them when mounting.

Have a look at this gigantic post to see how you would use the permissions, dmask and fmask fstab options to set permissions on mounting your ntfs partition.

[http://ubuntuforums.org/showpost.php?p=1653968&postcount=1](http://ubuntuforums.org/showpost.php?p=1653968&postcount=1)

---

### Post by bobman321123 on 2012-10-18
That did it, thanks :)

---

