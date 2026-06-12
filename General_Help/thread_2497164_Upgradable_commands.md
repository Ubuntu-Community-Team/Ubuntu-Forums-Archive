---
title: "Upgradable commands"
date: 2024-04-25
forum: General Help
---

### Post by dalpets on 2024-04-25
When I 'sudo apt update' I am told there are 3 packages that can be upgraded. The system then tells me to run 'apt list --upgradable' to see them. The 3 packages for upgrade are Python Jammy related & versions are cited. 

I get the impression that there may be security issues here that may require free Ubuntu Pro access but I am not sure. 

What format does the actual upgrade command take?
Thanks

---

### Post by wyattwhiteeagle on 2024-04-25
> **dalpets said:**
> When I 'sudo apt update' I am told there are 3 packages that can be upgraded. The system then tells me to run 'apt list --upgradable' to see them. The 3 packages for upgrade are Python Jammy related & versions are cited. 

I get the impression that there may be security issues here that may require free Ubuntu Pro access but I am not sure. 

What format does the actual upgrade command take?
Thanks
To upgrade, use
```
sudo apt upgrade
```

---

### Post by TheFu on 2024-04-25
> **dalpets said:**
> When I 'sudo apt update' I am told there are 3 packages that can be upgraded. The system then tells me to run 'apt list --upgradable' to see them. The 3 packages for upgrade are Python Jammy related & versions are cited. 

I get the impression that there may be security issues here that may require free Ubuntu Pro access but I am not sure. 

What format does the actual upgrade command take?
Thanks

**--upgradable** is added for enterprise users who want to know easily, which packages are going to be updated before they run those updates.  For home users, ignore it.
If you'd like to know exactly what any **apt** option does, those are documented in either the **apt**  or the **apt-get** manpages
From my local apt manpage (yours may be a different version):

```
       update (apt-get(8))
           update is used to download package information from all configured sources. Other commands operate on this data to e.g.
           perform package upgrades or search in and display details about all packages available for installation.

       upgrade (apt-get(8))
           upgrade is used to install available upgrades of all packages currently installed on the system from the sources configured
           via sources.list(5). New packages will be installed if required to satisfy dependencies, but existing packages will never
           be removed. If an upgrade for a package requires the removal of an installed package the upgrade for this package isn't
           performed.

       full-upgrade (apt-get(8))
           full-upgrade performs the function of upgrade but will remove currently installed packages if this is needed to upgrade the
           system as a whole.
...
       list
           list is somewhat similar to dpkg-query --list in that it can display a list of packages satisfying certain criteria. It
           supports glob(7) patterns for matching package names as well as options to list installed (--installed), upgradeable
           (--upgradeable) or all available (--all-versions) versions.


```
Always use local manpages, since they are included when the package is installed and have the _correct documentation FOR YOUR SYSTEM_, not mine.  That's important.

---

