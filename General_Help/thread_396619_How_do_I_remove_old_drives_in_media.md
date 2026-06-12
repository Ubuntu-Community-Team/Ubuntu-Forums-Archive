---
title: "How do I remove old drives in /media?"
date: 2007-03-29
forum: General Help
---

### Post by BartAfterDark on 2007-03-29
I have a problem with the /media folder. After I installed the latest updates it has more then one link to the drives. Showing like Data__ etc. How can I remove all, so they get re-added upon next restart?

Ie. See the picture :-)

 - Lars (one happy Ubuntu user)

---

### Post by taurus on 2007-03-29
Can you post your /etc/fstab here?

Applications -> Accessories -> Terminal
```
cat /etc/fstab
```

---

### Post by BartAfterDark on 2007-03-30
sure :-)

```
proc /proc proc defaults 0 0
# Entry for /dev/sdc1 :
UUID=c315b26a-da28-4510-91a1-7d6e4271b487 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sdc5 :
UUID=d677e088-9342-4b2d-b0a3-42a417fcbf87 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sdb2 /media/Backup ntfs-3g defaults,locale=da_DK.UTF-8 0 0
/dev/sdb1 /media/Movies ntfs-3g defaults,locale=da_DK.UTF-8 0 0
/dev/sda2 /media/Data ntfs-3g defaults,locale=da_DK.UTF-8 0 0
```

---

### Post by taurus on 2007-03-30
Either remove it from a commandline

```
sudo rmdir /media/"Data_"
```
or use nautilus.

```
gksudo nautilus
```

---

### Post by BartAfterDark on 2007-04-01
Great taurus ;-)

Thank You very much

---

