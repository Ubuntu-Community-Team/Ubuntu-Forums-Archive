---
title: "VMware uninstall -- it doesn't!"
date: 2007-02-16
forum: General Help
---

### Post by gjtoth on 2007-02-16
I attempted an install of VMware from Synaptic a little bit ago.  To make a long story short, it broke.  So, I attempted to uninstall it.  It APPEARS to go smoothly however, when I attempt to install anything else or during updates, the procedure moves along and then I get this error and the procedure shuts down.

E: /var/cache/apt/archives/vmware-player-kernel-modules-2.6.20-8_2.6.20.2-8.6_i386.deb: subprocess new post-removal script returned error exit status 1
E: /var/cache/apt/archives/vmware-tools-kernel-modules-2.6.20-8_2.6.20.2-8.6_i386.deb: subprocess new post-removal script returned error exit status 1

I've tried the --purge remove stuff and that gives me the same error.  I've tried apt-get install -f with the same error.

What do I need to do to clear this vicious error and get back to normal?

---

### Post by gjtoth on 2007-02-16
This is how I did it:

-  Opened Gnome Commander and did a search for "vmware*"
-  Deleted anything to do with VMware.
-  Opened a console and did "apt-get -- purge  remove" and then "apt-get install -f"

---

