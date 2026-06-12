---
title: "GRUB changes after getting UBUNTUupdates"
date: 2007-02-22
forum: General Help
---

### Post by tworthen on 2007-02-22
Ubuntu 6.1
Dual Boot With Win Xp
After Booting Into Ubuntu
Then Getting The Latest Ubuntu Upgrades
Two Additional Selections Identical To Two That Are Already There, Are Added To The Grub Selection Menu
I Edit Them Out And Save The Menu.lst File.
Everything's Fine Util The Next Time I Click On The Ubuntu Upgrade, Then The Same Thing Happens Again.
What's Up?  Highly Annoying
Thanks In Advance
Tom In San Diego Ca

---

### Post by dcstar on 2007-02-22
> **tworthen said:**
> Ubuntu 6.1
Dual Boot With Win Xp
After Booting Into Ubuntu
Then Getting The Latest Ubuntu Upgrades
Two Additional Selections Identical To Two That Are Already There, Are Added To The Grub Selection Menu
I Edit Them Out And Save The Menu.lst File.
Everything's Fine Util The Next Time I Click On The Ubuntu Upgrade, Then The Same Thing Happens Again.
What's Up?  Highly Annoying
Thanks In Advance
Tom In San Diego Ca

I doubt that the entries are "identical", if an update installs a new kernel then there will be an entry for the new kernel and an entry for the previous version.

Part of the process of installing updates is to ensure that installed kernels are reflected in Grub, if you no longer want a kernel, then remove the package using the tools provided.

---

