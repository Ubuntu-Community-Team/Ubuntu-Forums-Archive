---
title: "Plotting complex GIS data kills X windows"
date: 2008-03-28
forum: General Help
---

### Post by thk on 2008-03-28
I'm wondering if anyone else has been having problems with X-windows crashing in Gutsy when plotting large numbers of polygons. The problem appears with QGIS and when plotting the same data in R using "sp" classes. (If you don't know what that means, it is all related to Geographic Information Systems.) The data in question is a subset of the GSHHS coastline dataset. I'm happy to share the shapefile if others want to try to replicate the bug.

---

### Post by rhyshowitt on 2008-04-13
I have the same experience.  I am having particular trouble in editing any large QGIS dataset (specifically a shapefile of a contour map).

No idea where to go from here.

Running Hardy Beta v16, which seems to be causing me a number of problems.  At present I don't have the time or technical skill to sort out, sorry.

Rhys

---

### Post by thk on 2008-04-13
Unfortunately, at least in my case, the bug is in the polygon filling code in Xorg. That code is 20+ years old! I have filed bugs with launchpad and bugzilla.freedesktop.org. I believe there is also a bug filed against QGIS as well. I think once Hardy gets stable, I am going to stick with it for awhile.

---

