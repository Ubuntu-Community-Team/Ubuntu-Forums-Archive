---
title: "vmware server install gone  very bad, now I cant update system!"
date: 2007-04-28
forum: General Help
---

### Post by Dj_Extreme_Audiophile on 2007-04-28
I was unsuccessful in installing vmware server, now when i go to synaptic to update the system I get this error:


Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package vmware-server needs to be reinstalled, but I can't find an archive for it.'

Any help would be much appreciated! 

-John

---

### Post by fwojciec on 2007-04-28
Did you try uninstalling the vmware server?  The installer installs the script to do it, which should be installed even if the installation failed - you can run it by typing

sudo perl /usr/bin/vmware-uninstall.pl

(not sure if this is the best way to run it, but it worked for me)

Then you should also delete the contents of the /etc/vmware directory, and maybe also the vmware script from the /etc/ini.d directory (if it is there)

---

### Post by Dj_Extreme_Audiophile on 2007-04-28
I actually ran that uninstall before you suggested it, it ran and completed.
and those other files were non-existing that you suggested,

I am still getting that same message from synaptic. I have even made a new  sources.list in hopes that it would fix it. No dice :(
I feel like i am in a real pickle! Ive rebooted and ive scoured google for over 2 hours now trying to find a solution!

---

### Post by zvacet on 2007-04-28
If you want to uninstall it go to the **etc** and delete vmware folder.

---

### Post by Dj_Extreme_Audiophile on 2007-04-28
there were no traces of vmware in the /etc folder

---

### Post by yopnono on 2007-04-28
> **Dj_Extreme_Audiophile said:**
> there were no traces of vmware in the /etc folder

Open the search and search for vmware in "contains the text"
Then edit the files that have this entry.

---

### Post by Dj_Extreme_Audiophile on 2007-04-28
agh, no dice,

I think Im just gonna do a clean install of ubuntu.

---

### Post by yopnono on 2007-04-28
> **Dj_Extreme_Audiophile said:**
> agh, no dice,

I think Im just gonna do a clean install of ubuntu.

Have a look in the```
 /var/lib/dpkg
``` folder there is where the synaptic store it's info.

---

