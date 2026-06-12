---
title: "WINE from Synaptic"
date: 2005-07-31
forum: General Help
---

### Post by jsimmons on 2005-07-31
I was going to install WINE through synaptic, but weird stuff is happening.  I want to make sure I get their latest config tool, but it's unclear as to which one is the latest (Package managers really have to imrpove the package descriptions that show up in synaptic).

If I have "wine" (20050725) marked for installation, and then select "winesetuptk" for installation, it unselects "wine".

There's also another config tool listed in synaptic (I assume it's an alternative to "winesetuptk") which does not un-select "wine".  

What should I do to install wine with their latest and greatest configurator?

---

### Post by az on 2005-07-31
winesetuptk is depreciated.


Install wine, wineutils and libwine.  From the backports repository, install winetools.


Winetool is the recommended wine configuration tool.

---

