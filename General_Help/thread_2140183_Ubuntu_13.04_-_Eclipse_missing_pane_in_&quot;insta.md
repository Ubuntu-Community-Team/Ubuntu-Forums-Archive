---
title: "Ubuntu 13.04 - Eclipse missing pane in &quot;install new software &quot;"
date: 2013-04-28
forum: General Help
---

### Post by TJSL on 2013-04-28
I cannot use install new software using "help -> install new software" in Eclipse (both 4.2 and 3.8) after upgrading to Ubuntu 13.04.  The panel below the Name/Version bar appears to be missing (or too small) to list the available software.  When scrolling on the side of the missing panel, it is possible to see a handful of rows of pixels change, which I believe are the items in the list of available software scrolling past.  It is not possible tell for sure, however, becasue if the panel exists at all, it is likely only a few pixel rows high.  This is true with both Eclicps 4.2 (which I installed manually) and Eclispe 3.8 (which I installed from the Ubuntu Software Center after removing Eclipse 4.2).
.
Thanks!

---

### Post by TJSL on 2013-05-02
I have found two contributing factors to this problem.  First, I noticed that the Eclipse -> Help -> Install New Software window was not maximized.  Maximinzing the window provided enough vertical height for item in the list to be displayed.  I would prefer to see several items in the list, rather than only a single item in the list at a time, but at least it is possible to select packages to install.  Second, I was using the defalt Nouveau display driver.  I noticed that the computer screen scrolled when moving the cursor between the top and bottom of the screen.  This occured because the Nouveau driver appartently cannot support my screen resolution (i.e., 1366 X 768).  Installing the NVIDIA binary display driver and selecting the proper resolution eliminated the need for the screen to scroll.

---

