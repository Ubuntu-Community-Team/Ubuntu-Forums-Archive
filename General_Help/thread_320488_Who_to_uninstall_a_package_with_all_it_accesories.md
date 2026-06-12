---
title: "Who to uninstall a package with all it accesories?"
date: 2006-12-17
forum: General Help
---

### Post by october1917 on 2006-12-17
I installed a package yesterday via apt-get and i saw that it downloaded many extra packages needed to run. I now want to unisntall it but i don't want to leave hangovers.

So is there a command to uninstall the package and all the extra packages that it installs?

---

### Post by aysiu on 2006-12-17
If you're using Edgy Eft, you can do this: ```
sudo apt-get autoremove *application*
``` If not, then you'll have to use *deborphan* or *gtkorphan* to find the unused dependencies and remove them one by one. In the future, you may want to use *aptitude* instead of *apt-get*. More explanation here:
[http://psychocats.net/ubuntu/aptitude](http://psychocats.net/ubuntu/aptitude)

---

### Post by october1917 on 2006-12-17
Thank you. 

Yes i'm using Edgy Eft
writing autoremove it will uninstall all the extras installed during its installation?

---

### Post by aysiu on 2006-12-17
> **october1917 said:**
> Thank you. 

Yes i'm using Edgy Eft
writing autoremove it will uninstall all the extras installed during its installation?
Yes, it should. If not, then you'll have to use *gtkorphan* to get rid of the unused dependencies.

---

