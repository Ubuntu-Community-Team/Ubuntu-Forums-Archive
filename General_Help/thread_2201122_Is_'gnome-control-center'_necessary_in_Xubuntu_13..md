---
title: "Is 'gnome-control-center' necessary in Xubuntu 13.10?"
date: 2014-01-22
forum: General Help
---

### Post by EnglishElectricAndy on 2014-01-22
This thread has been stimulated by my research into trying to solve an issue posted in another thread. 

After a recent upgrade (via a Live Session running off a bootable USB) everything seemed to go smoothly initially, however I'm finding more and more peculiarities that seem to be traceable back to the gnome-control-center package.

Is it possible to safely purge this package? Please bear in mind I'm using Xubuntu and not full-flavour Ubuntu.

---

### Post by ajgreeny on 2014-01-22
What happens if you try to remove it?  If it says that **xubuntu-desktop** will also be removed it is not a major problem as that is just a meta-package and contains only a list of packages needed for a full default xubuntu desktop system.  That package is needed only if you are going to upgrade distro version, eg, from 13.10 to 14.04

I have not used 13.10, but if it is like 12.04 it has the **settings-manager** application which is very like gnome-control-centre, allowing the setting of most of the hardware configuration in your system.

---

