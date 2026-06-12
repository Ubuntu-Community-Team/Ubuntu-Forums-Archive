---
title: "How do I save current wifi driver before compiling a new one?"
date: 2008-03-07
forum: General Help
---

### Post by rockhoppr on 2008-03-07
I want to compile and install a new version of the madwifi drivers but I want to be able to revert back to my known good versions if I need to. How do I do that? How do I save the one's currently in use and roll back after I try the new ones?

Thanks!

---

### Post by uberlube on 2008-03-07
Im not sure why you want to do this? Are your current driver not working? If you want to install new ones just disable the one you are currently using with ndiswrapper. But don't delete them, keep them in the folder they are already in. And if the new driver doesn't take just reinitialize the original ones.

---

### Post by rockhoppr on 2008-03-07
I want/need to do it because I'm studying network security and want to try out the aircrack-ng toolset. Unfortunately the stock madwifi drivers aren't able to do packet injection so I need to patch and recompile them.

Plus, swapping driver versions is probably a fundamental skill I should have.

---

