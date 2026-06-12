---
title: "Fix for large fonts in firefox"
date: 2008-05-08
forum: General Help
---

### Post by Choad on 2008-05-08
i just remembered a little tweak and seeing as the bug remains in hardy i'll post it here

if you change your monitor's screen resolution, firefox throws a tantrum and makes the fonts huge. well, firefox 3 is a little better... it used to be all fonts and images, now it's just some fonts.

anyway

1. type about:config
2. acknowledge that there are in fact dragons in this web page
3. in the filter bar, type "dpi"

here you should see just 1 result "layout.css.dpi" and the default value is -1 (auto detect, one presumes). you just gotta change the value for the dpi of your monitor. it's not going to melt your computer if you get it wrong so don't be afraid to experiment if you don't know it. mine looks good with a value of 90.

---

