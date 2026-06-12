---
title: "[SOLVED] Where do programs install?"
date: 2007-12-14
forum: General Help
---

### Post by A-dogg on 2007-12-14
I downloaded grsync from the repository (front-end for the rsync backup tool) and it didn't add it to the menu. I want to add it, but I can't find out where it installed to. I've used the search panel applet but the only option that gives me is to run grsync, but it won't take me to the folder where it's installed. Is there a default place downloaded programs are installed?

Thanks!

---

### Post by Tenken on 2007-12-14
Try this command:
```
cd /
whereis grsync
```

it should give you the location of config files, binaries, etc.

Hope that helps

---

### Post by PmDematagoda on 2007-12-14
Some applications may not be in the Main Menu either because they may not have a GUI or can be used to make a lot of changes. I believe you can bring Grsync using Main Menu in System>Preferences>Main Menu and looking at the Accessories or System Tools sections, if it cannot be found there then you can make a new Main Menu entry for Grsync using the same tool.

---

### Post by A-dogg on 2007-12-14
thanks!

---

