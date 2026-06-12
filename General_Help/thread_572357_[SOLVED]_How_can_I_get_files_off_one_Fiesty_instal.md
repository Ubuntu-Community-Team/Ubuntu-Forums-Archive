---
title: "[SOLVED] How can I get files off one Fiesty installation from another?"
date: 2007-10-10
forum: General Help
---

### Post by apple_and _linux on 2007-10-10
OK, here's the deal:  ever since I enabled root login through the GDM, I haven't been able to boot Ubuntu.  So, I wrote over my XP partition and reinstalled it.  Now I have a working installation (from which I am now typing) and a non-working installation (the old one.)  I have been able to recover some files from the old installation, but some of what I want, I can't get access to.  For example:  I can see where the Mozilla Thunderbird folder is in my home folder, but it's got the "little red X" on it and I can't open it.  Is there any way I can overrule these permissions to copy such items?  Thanks for any help.
Oh yeah, and I've already tried using "gksudo nautilus".  With that, I can only see the home partition.

---

### Post by DaGrimReefah on 2007-10-10
In terminal, type "sudo chmod 777 /directory/of/files".

---

### Post by apple_and _linux on 2007-10-10
Thanks!  This let me get what I needed.

---

