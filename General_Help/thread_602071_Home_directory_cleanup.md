---
title: "Home directory cleanup"
date: 2007-11-03
forum: General Help
---

### Post by sicofante on 2007-11-03
[FONT=Tahoma]Installing and uninstalling software in Ubuntu looks a lot safer than doing the same in Windows and I appreciate that. However, I have realized my home directory has grown in hidden directories.

Is there a way to cleanup that in an automatic way? Sort of a scanner that would check for installed software and related .* directories and ask if you want to keep them or delete them?
[/FONT]

---

### Post by haldean on 2007-11-04
If you open up Synaptic (this is assuming you're using Ubuntu and not Kubuntu... I don't know how to do it in Adept), press Status in the bottom left, then click "Not Installed (Residual Config)". Those are all packages that you've installed before which have left configuration files behind. If you want to remove any of them, you can just right click it and click "Mark for Complete Removal", which will... well... mark it to be completely removed :D

---

