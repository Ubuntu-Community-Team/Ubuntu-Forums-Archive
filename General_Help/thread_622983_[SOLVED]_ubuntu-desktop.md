---
title: "[SOLVED] ubuntu-desktop"
date: 2007-11-25
forum: General Help
---

### Post by benny bronx on 2007-11-25
Hi:

   I experienced a problem while trying to play wmv. files in opera.  File-roller would produce a message saying that the format is not supported.  I searched the forum for an answer but did not find one.  So I replaced file-roller with karchiver and all seems well.  However, when uninstalling file-roller, I also had to uninstall ubuntu-desktop.  I know this is needed for upgrades, but since I do fresh installs, I don't need it for that reason. My question; "is there any other reason I should not remove ubuntu-desktop?

---

### Post by aysiu on 2007-11-25
No. There is no other reason to keep *ubuntu-desktop*.

Honestly, though, you can use KArchiver without uninstalling File-Roller. Are you hard up for hard drive space? I think it'll free up a few thousand kB of space: ```
sudo apt-get remove file-roller
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  file-roller thunar-archive-plugin
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking **5259kB** disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
```

---

### Post by benny bronx on 2007-11-25
Thanks for the quick reply.  No, Space is not an issue, but I originally had both and made (I think) karchiver the default app and the problem was still there.  I am looking at your terminal window and I don't see ubuntu-desktop.  I uninstalled with synaptic.  Would that make a difference?

---

### Post by aysiu on 2007-11-25
> **benny bronx said:**
> Thanks for the quick reply.  No, Space is not an issue, but I originally had both and made (I think) karchiver the default app and the problem was still there.  I am looking at your terminal window and I don't see ubuntu-desktop.  I uninstalled with synaptic.  Would that make a difference?
Sorry. I don't have *ubuntu-desktop* installed, which is why it wasn't marked for removal.

---

### Post by benny bronx on 2007-11-25
Again, thanks.  My main question was answered so I consider this resolved.

---

