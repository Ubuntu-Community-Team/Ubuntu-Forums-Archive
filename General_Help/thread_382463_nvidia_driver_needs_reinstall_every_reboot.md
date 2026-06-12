---
title: "nvidia driver needs reinstall every reboot"
date: 2007-03-12
forum: General Help
---

### Post by CocoAUS on 2007-03-12
Since the custom linux-restricted-modules repo went down, I rebuilt my machine, and I had to install nVidia from the official site.  When I installed 9746, the driver simply wouldn't work.  I installed the latest (9755), and it worked.  Sort of.  Every time I boot my machine, I have to reinstall via the .run package for the driver to work, or else I get the blue screen of X errors.  What the EFF is going on?

---

### Post by theslut on 2007-03-12
from memory you need to have the x11 sources installed and the kernel sources otherwise every time you reboot it complains it didn't find something.

i get this problem every time i install the drivers with default ubuntu but installing the correct source files from the repos sorts it out.

sorry i can't be more specific.

---

