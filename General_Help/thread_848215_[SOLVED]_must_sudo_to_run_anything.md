---
title: "[SOLVED] must sudo to run anything?"
date: 2008-07-03
forum: General Help
---

### Post by sunmorgus on 2008-07-03
My ubuntu installation (via wubi) was running fine yesterday, now however, after installing vmware workstation 6.0.4 (not sure if this has anything to do with it) i have to run any program with sudo from the terminal in order for it to work properly. Take firefox for example...if i simply click on the firefox icon, it loads, but none of my profile settings are there. if i sudo firefox, everything come up properly. same goes for vmware...if i run normally, it acts as though starting it for the first time everytime, and cant access my home drive; however, if i sudo it from terminal it runs and can access my home drive...any suggestions on how to fix this?

---

### Post by chrisccoulson on 2008-07-03
Running graphical applications with sudo may cause that application to write files to your home folder which belong to the root user. If you then attempt to run the application without sudo, it may not be able to write to your user profile, as it is owned by root.

It might be that your home folder or some critical files/folders within it have become owned by root. Try this in a terminal:
```
sudo chown -R <*user_name*>:<*user_name*> /home/<*user_name*>
```
..where <*user_name*> is your user name

---

### Post by sunmorgus on 2008-07-03
That did it, thank you!

---

