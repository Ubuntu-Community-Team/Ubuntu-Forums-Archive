---
title: "Cube? want 2 desktops back..."
date: 2008-05-30
forum: General Help
---

### Post by woodrrow on 2008-05-30
i typed:
gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4

gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1

trying to get cube to work.. well I just want my 2 desktops back. How do I do that?

thanks

---

### Post by Forlong on 2008-05-30
First of all, use ccsm (sudo apt-get install compizconfig-settings-manager) to do such things. Gconf is way too laborious for that.

But here's how to do it in Gconf anyway:
```
gconftool-2 -s -t int /apps/compiz/general/screen0/options/hsize 2
```

---

