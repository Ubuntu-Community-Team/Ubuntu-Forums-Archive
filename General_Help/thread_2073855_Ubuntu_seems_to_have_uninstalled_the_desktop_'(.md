---
title: "Ubuntu seems to have uninstalled the desktop :'("
date: 2012-10-20
forum: General Help
---

### Post by bbno3 on 2012-10-20
Ubuntu 12.04 i have had trouble installing the new ubuntu and i thought it was about to upgrade but then it said something about removing unity and now i cant get ANY menus what so ever and the top bar isn't there. nothing works i can open a terminal and firefox is by default to open on startup. i have no idea what's happened but i dont want to do a clean install and i have important files which i CANT back up since i dont have the memory or storage to do so. and also firefox won't open up new windows :'(

---

### Post by offgridguy on 2012-10-20
A new install doesn't have to be a complete wipe of what is already on your hard drive, you can install
alongside of whats already there,  assuming that you have enough partitions left for that.

---

### Post by bbno3 on 2012-10-20
> **offgridguy said:**
> A new install doesn't have to be a complete wipe of what is already on your hard drive, you can install
alongside of whats already there,  assuming that you have enough partitions left for that.

Ahhh so i can install a new partion of Ubuntu and then transfer files over and delete the other partion? and then use a partion editor to increase the size of the new Ubuntu install?

---

### Post by offgridguy on 2012-10-20
> **bbno3 said:**
> Ahhh so i can install a new partion of Ubuntu and then transfer files over and delete the other partion? and then use a partion editor to increase the size of the new Ubuntu install?
Transfering files from one partition to another is something i can't advise on, hopefully someone more knowledgable will jump in here.
Rather than increasing the size of the partition  I would make it large enough initially to
handle all the anticipated data you would put on it.  Sorry I couldn't be of more help.

---

### Post by bbno3 on 2012-10-21
Bump

---

### Post by rudeboyskunk on 2012-10-21
Did you install/update a new graphics driver?  What exactly were you doing right up until this happened?

---

### Post by MG&amp;TL on 2012-10-21
> **bbno3 said:**
> Ubuntu 12.04 i have had trouble installing the new ubuntu and i thought it was about to upgrade but then it said something about removing unity and now i cant get ANY menus what so ever and the top bar isn't there. nothing works i can open a terminal and firefox is by default to open on startup. i have no idea what's happened but i dont want to do a clean install and i have important files which i CANT back up since i dont have the memory or storage to do so. and also firefox won't open up new windows :'(

If the upgrade removed unity, that's what's going to happen. :) Just open a terminal and run:

```
sudo apt-get install ubuntu-desktop
```

and see what happens. Post it back here.

---

