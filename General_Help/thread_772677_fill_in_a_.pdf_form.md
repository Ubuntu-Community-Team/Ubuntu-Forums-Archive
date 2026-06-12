---
title: "fill in a .pdf form"
date: 2008-04-28
forum: General Help
---

### Post by gregwm on 2008-04-28
i found myself wrestling with various .pdf software, all because i prefer to avoid cutting trees or supporting m$, and i blithely presume available open source software would make it easy to fill in forms.  well i arrived finally, but folks might appreciate hearing about the journey.  i received a form to fill out:  [http://scalliondata.com/CommercialMaterials_EnergyStarBuildingWorksheet.pdf](http://scalliondata.com/CommercialMaterials_EnergyStarBuildingWorksheet.pdf)

evince-gtk 2.20.1-0ubuntu1 failed to display most of it.
xpdf-3.00-14.el4 displayed it fine.
pdfedit 0.3.1-1 seemed happy to add text, but
acroread-5.0.10-1.2.el4.rf failed to show the text that pdfedit had added.
convert (imagemagick 7:6.2.4.5.dfsg1-2ubuntu1) assessed pdfedit's output as 'damaged'.
gimp 2.4.2-0ubuntu0.7.10.1, like evince, failed to show most of the original.
scribus 1.3.3.9.dfsg-1ubuntu1 couldn't open it, complaining "not an acceptable format".
flpsed 0.3.7-1.1ubuntu2 fussed "Please install ghostscript and make sure 'gs' is in the PATH." (but it is installed and indeed on the PATH).
convert happily converted the original pages to .jpg's, which i then used as backgrounds in
openoffice.org-common 1:2.3.0-1ubuntu5.3, the only limitation being i don't see how to do more than 2 differing page backgrounds in a single OOo text document.

---

