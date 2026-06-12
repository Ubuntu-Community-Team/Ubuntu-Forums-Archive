---
title: "Deinstalling unneeded dependencies"
date: 2008-04-27
forum: General Help
---

### Post by Lars Stokholm on 2008-04-27
When installing a software package, some dependency packages are often installed along with it. Deinstalling the "primary" packages though, will leave behind potentially unneeded dependency packages on the system.

Is there a way to find and deinstall those packages?

What Portmaster for FreeBSD does, is it spots if certain packages are made "leaf packages" on deinstallation of the "primary" package. If that is the case, it asks the user to deinstall those aswell - it continues this untill no packages are made leaf.

---

### Post by vanadium on 2008-04-27
"sudo apt-get clean" does remove unneeded dependencies, and it can also be done from the graphical tool, Synaptic package manager.

---

### Post by rubicon on 2008-04-27
Sorry, apt-get clean does not clean dependencies. It cleans local package repository.

apt-get autoremove actually do remove unneeded dependencies.

---

### Post by Lars Stokholm on 2008-04-27
In terms of Synaptic, will autoremove "remove" the packages or "completely remove" them?

---

### Post by laero on 2008-04-27
Or if you want to use Synaptic you can click the "status" button in the lower left corner and then above it click the title thats says something like "packages that can be auto-removed".

---

### Post by rubicon on 2008-04-27
Just *remove*. If you want to fully remove (purge) these packages, you need to run ```
sudo apt-get autoremove --purge
```

I beieve so :)

---

