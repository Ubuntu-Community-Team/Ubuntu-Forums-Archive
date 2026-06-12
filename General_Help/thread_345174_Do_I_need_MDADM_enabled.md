---
title: "Do I need MDADM enabled?"
date: 2007-01-23
forum: General Help
---

### Post by undeadsoldier on 2007-01-23
Hi Guys,

I hope somebody can give me a quick answer to this, I have the MDADM service enabled on my debian box, and I'm just wondering if I need it enabled or not?

I only have one HDD and no RAID, so do I really need MDADM?

Cheers. ):P

---

### Post by kuja on 2007-01-23
You only need mdadm if you're using LVM or RAID, else, feel free to remove or disable it.

---

### Post by rimvydukas on 2007-01-27
But mdadm depends on ubuntu-standard which is not recommended to remove:(

---

### Post by Ramses de Norre on 2007-01-27
You can install sysv-rc-conf to disable all unneeded services.

---

### Post by rimvydukas on 2007-01-27
I can't understand only one thing - why mdadm and lvm packages depend on ubuntu-standard package? Because of this I'm not sure if I can sefaly remove mdadm and lvm packages:( They both depend on ubuntu-standard and ubuntu-standard package is not recommended to remove. I'm lost a little with ubuntu in this place, there was no such dependencies in Debian:(

---

### Post by Ramses de Norre on 2007-01-27
Ubuntu-standard is a metapackage, it has no contents but it has several other packages as dependency. the purpose is to be able to install ubuntu-standard and all "standard" packages are automatically installed as dependency.
When you uninstall one of those "dependencies" however, the metapackage gets uninstalled too, but all other packages remain on your system.
So you can safely remove ubuntu-standard, but you'll need to reinstall it when you dist-upgrade to a new version (because often new packages will be supposed to be pulled in by an installed metapackage).
You can also keep the package installed and use a tool like sysv-rc-conf to disable the service so it wont startup and use cpu cycles and memory.

---

### Post by rimvydukas on 2007-01-27
Is this ubuntu-standard package required only for dist-upgrade and not for lets say aptitude upgrade? 

I'm not very sure about this description:

--------------
 It is safe to remove this package if some of the standard system packages are not desired.  However, it is recommended that you
 keep it installed, because it is used to carry out certain upgrade transitions (such as adding new packages to the system).
--------------

---

### Post by kuja on 2007-01-28
It certainly isn't required, whether it's going to be useful or not is dependent on what packages you want on your system, especially after a dist-upgrade. If you remove it, and then dist-upgrade later, then things will only be different if that metapackages dependencies have changed. They might, then again, they might not. If you are happy with things as is in the current version then you probably won't care if dependencies change in the new version.

---

