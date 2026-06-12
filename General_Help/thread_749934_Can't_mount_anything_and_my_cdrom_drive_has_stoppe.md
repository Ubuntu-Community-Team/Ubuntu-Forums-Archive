---
title: "Can't mount anything and my cdrom drive has stopped reading discs"
date: 2008-04-09
forum: General Help
---

### Post by davidcaiazzo on 2008-04-09
Not a good day for me, first I had my kubuntu problem now it seems like I have screwed something else up. Anyway after I uninstalled the ubuntu desktop(via removing all the packages and then reinstall ubuntu-desktop to reinstall whatever was in the cross fire) I have discovered that I can no longer mount iso images or read cds. The cd drive is listed in computer:\\\ it just doesn't do anything. Any ideas? My laptop is a Lenovo T60p

---

### Post by davidcaiazzo on 2008-04-09
Stupid me I figured out the problem just after I posted this. Anyway for anybody that has a similiar problem in the future just do this:
```

$ sudo rm /etc/rc2.d/S13kdm
$ sudo mv /etc/rc2.d/S12hal /etc/rc2.d/S13hal

```

REMEMBER ONLY DO THIS IF YOU _**REMOVED**_ KDE OR THE KUBUNTU-DESKTOP PACKAGE!

---

