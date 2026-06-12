---
title: "Network Printer Sharing"
date: 2007-04-28
forum: General Help
---

### Post by thompa on 2007-04-28
Hi there,

Using Ubuntu Dapper and revisiting printer and file sharing which I couldn't get to work last time I tried.

I now have file sharing working across the network using Samba after working out how to get around the permission issue -  but I can't get the printer sharing working.
I thought that I would start afresh and download CUPS again because there seemed to be something amiss with printer.conf ... but came up with this error in Synaptic:-

E: cupsys: subprocess post-installation script returned error exit status 2
E: hplip: dependency problems - leaving unconfigured
E: printconf: dependency problems - leaving unconfigured
E: cups-pdf: dependency problems - leaving unconfigured

I have Ubuntu loaded onto a separate partition - is this causing the problem? Should I reformat the hard drive again and get rid of the partition? The partition seems to cause more problems than it solves!

thanks in anticipation.

Allan

---

### Post by bburgin on 2007-05-09
I'm using 6.06 Dapper running Gnome GUI. This is how I resolved the same cups subprocess script error.   Try in Synaptic Package Manager to completely uninstall "cupsys" and "gnome-cups-manager".  Reload the package manager and then reinstall "cupsys" and "gnome-cups-manager"

---

