---
title: "uninstall a program along with dependencies"
date: 2007-09-30
forum: General Help
---

### Post by Chymera on 2007-09-30
ok, so i installed this application, but, along with it, i also had to install 2 or 3 dependencies ....

now i want to get rid of the program, and those dependencies i needed in order to make it work. However i do realize that the program also had a lot of other dependencies, only those were already installed; consequently, deleting ALL of the programs dependencies might mess up my system....  i still have the original .deb from which i installed it.... is there any way to trace exactly what i installed along with it and get rid of it?

---

### Post by mcduck on 2007-09-30
You can just run 'sudo apt-get remove --auto-remove packagename' to install the package and all the packages that were installed with it as dependencies. This will not remove _all_ dependencies, only those that were installed automatically when you installed the package.

You can also just check the autoremovable packages with Synaptic, and then mark them for removal.

---

### Post by aJayRoo on 2007-09-30
Well, I think when you install a deb file apt will track the dependencies for you, which means you should be able to use:
```
sudo apt-get autoremove
```
to remove dependencies that are no longer needed. I'm pretty sure it should work like that but I could be wrong.

---

### Post by Chymera on 2007-09-30
> **mcduck said:**
> You can just run 'sudo apt-get remove --auto-remove packagename' to install the package and all the packages that were installed with it as dependencies. This will not remove _all_ dependencies, only those that were installed automatically when you installed the package.

You can also just check the autoremovable packages with Synaptic, and then mark them for removal.

so i just write the name of the deb package as in hhjdhd_hadjkhad_5.1.2.3.3.deb or just the name of the package itself (package as in program) like hhjdhd-hadjkhad

---

### Post by mcduck on 2007-10-01
> **Chymera said:**
> so i just write the name of the deb package as in hhjdhd_hadjkhad_5.1.2.3.3.deb or just the name of the package itself (package as in program) like hhjdhd-hadjkhad

Name of the package itself. As in 'sudo apt-get remove --auto-remove hhjdhd-hadjkhad'

---

