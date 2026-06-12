---
title: "There were 2 icons of each Libre Office program in dash"
date: 2020-07-21
forum: General Help
---

### Post by mickee384 on 2020-07-21
The other day I notice when pressing Super key, and also clicking on the applications that there were 2 icons of each Libre Office application, with 2 different versions. Like 2 Writers etc. Took me a while to figure out why. Turns out when I used the software install to install (thought it would update current installation), I installed the snap (that was the only Libre Office there). In any case I assume because it was a snap pkg, it installed Libre Office along side the current installed office pkg. Before I figured this out I tried looking in Synaptic, but only the current version showed up there. When I used apt to remove libreoffice, it uninstalled the current version and the "new" version remained. This new version (installed from snap) didn't get the theme that everything else used either. Nor did it have an icon in Cairo Dock. I use a dark theme and it was blindingly light. So if you find that you have 2 Libre Offices and only one shows up in Synaptic, it likely means you installed a snap version. They seem to play by their own rules.

---

