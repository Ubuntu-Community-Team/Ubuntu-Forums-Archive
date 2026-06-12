---
title: "Deleting Folders"
date: 2007-02-09
forum: General Help
---

### Post by Rhaddad on 2007-02-09
Hello,
can someone please tell me how i can remove or delete folders buy being a super user.

---

### Post by rich.bradshaw on 2007-02-09
just user rmdir in a terminal i.e.

sudo rmdir $nameofdir

ALternatively, load Nautilus as root

sudo nautilus

then you can delete what you want.

Be careful though.

---

### Post by taurus on 2007-02-09
And if the directory is not empty, them you need to run

```
sudo rm -rf **directory_name**
```
And if you want to run nautilus as root, please use gksudo instead of sudo.

```
gksudo nautilus
```
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

