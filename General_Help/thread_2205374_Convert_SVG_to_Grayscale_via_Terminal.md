---
title: "Convert SVG to Grayscale via Terminal"
date: 2014-02-13
forum: General Help
---

### Post by magikarp2 on 2014-02-13
I'm currently trying to convert an icon set to grayscale. I've written a bash script that will iterate over all the svg files but I cannot find how to convert them to grayscale. I did find that you could use inkscape via

*inkscape -f file.svg --verb=org.inkscape.color.grayscale --verb=FileSave --verb=FileClose*

But this means inkscape will open itself and perform the operation for every icon, before closing and re-opening to do the same with the next svg file. This takes far too long. What's a quicker way?

---

### Post by magikarp2 on 2014-02-15
Using imagemagick I can use *mogrify -colorspace gray *or *-type Grayscale* but they both produce produce an entirely black image. These commands do work with non svg files but the icons I want to change are in svg format.

---

