---
title: "deleting program files for uninstalling"
date: 2007-10-02
forum: General Help
---

### Post by elidoperezmd on 2007-10-02
hey all....

can i unistall a program completely just by deleting the program files?

---

### Post by 505 on 2007-10-02
No, because all files are scattered over the place. For example, most programs also install help files and config files. If you installed the program from a repository (or .deb. file), goto System->Adminitration->Synaptic and search for the program you want to uninstall. Then right-click and select remove.

---

### Post by elidoperezmd on 2007-10-02
im trying to uninstall google earth... there is no repository for it... installed it from a package... anu adavise?

---

### Post by Sunforge on 2007-10-02
There's mention of uninstalling Google earth here:

[http://ubuntuforums.org/showthread.php?t=195382](http://ubuntuforums.org/showthread.php?t=195382)

and here:

[http://ubuntuforums.org/showthread.php?t=548244&highlight=uninstall+google+earth](http://ubuntuforums.org/showthread.php?t=548244&highlight=uninstall+google+earth)

And this one which has a pretty elegant one line nuke which should get you out of jail:

[http://www.linuxquestions.org/questions/showthread.php?t=454805&page=2](http://www.linuxquestions.org/questions/showthread.php?t=454805&page=2)

---

### Post by Seisen on 2007-10-02
If it was a .deb file than all you would have to do is ```
sudo dpkg -r googleearth
```

---

