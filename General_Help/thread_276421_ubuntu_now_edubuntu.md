---
title: "ubuntu now edubuntu?"
date: 2006-10-12
forum: General Help
---

### Post by jeefreak on 2006-10-12
after intalling ubuntu i went through the synaptics package manager to install a few things.  i do not remember when i installed/updated but now it is loading edubuntu and not ubuntu.  is there anyway i can change this or revert back to the original install of ubuntu? thanks!

---

### Post by ciscosurfer on 2006-10-12
Just remove the package (choose your favorite package manager/gui.)  From the command line you can issue the following to remove the edubutu-desktop package, all on one line (just copy and paste)```
sudo aptitude update && sudo aptitude remove edubuntu-desktop
```

---

### Post by aysiu on 2006-10-12
Maybe this might help?
[http://doc.gwos.org/index.php/Change_Usplash](http://doc.gwos.org/index.php/Change_Usplash)

---

