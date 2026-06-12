---
title: "[SOLVED] Very slow start up after the update"
date: 2008-06-25
forum: General Help
---

### Post by btermeli on 2008-06-25
I use storage device manager to auto mount my HDD. it mounts my win and shared partition automatically, yesterday  shared partition suddenly dissapeared and shows only win partition on the desktop. How can I bring it back?

Thanx...

---

### Post by erginemr on 2008-06-27
Hi,

You can try installing the package **ntfs-config** and let it adjust /etc/fstab accordingly so that your NTFS partitions are automounted (provided that they are fixed, i.e. not removable). To achieve this, please do the following:

1. From a terminal;
```
sudo aptitude install ntfs-config
```

2. Then;
```
Alt+F2 -> gksu ntfs-config
```

3. Check both options in the dialog-box that appears.

4. Restart your system.

---

